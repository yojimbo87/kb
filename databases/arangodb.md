# ArangoDB

### Dump data

```
arangodump --server.database <db_name> --output-directory "<dump_folder>"
```

### Restore data

```
arangorestore --server.database <db_name> --input-directory "<dump_folder>"
```

### Connect to server with arangosh

```
arangosh --server.endpoint tcp://127.0.0.1:8529
```

### Change user password in arangosh

```
require("org/arangodb/users").update("my-user", "my-secret-password");
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

### List available user functions

```
require("org/arangodb/aql/functions").toArray();
```
