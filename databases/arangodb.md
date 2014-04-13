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
require("org/arangodb/aql/functions").register("myfunctions::temperature::celsiustofahrenheit",
function (celsius) {
return celsius * 1.8 + 32;
});
```
