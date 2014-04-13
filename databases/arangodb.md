### Dump data

```
arangodump --server.database <db_name> --output-directory "<dump_folder>"
```

### Restore data

```
arangorestore --server.database <db_name> --input-directory "<dump_folder>"
```

### Register AQL user function

```
require("org/arangodb/aql/functions").register("lion::POSITION",
function (list, search) { var i, n = list.length; for (i = 0; i < n; ++i) { if (list[i] === search) { return i; } } return -1; });
```

```
require("org/arangodb/aql/functions").register("lion::NTH",
function (list, position) { if (position < 0 || position >= list.length) { return null; } return list[position]; });
```
