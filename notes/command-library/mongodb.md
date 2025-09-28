---
layout: page
title: MongoDB
permalink: /notes/command-library/mongodb/
---

- Connect to MongoDB with url
```
mongo dtlprod4:29031
```

- Display all the databases
```
show dbs
```

- Select a specific database (e.g. brt) for use
```
use brt
```

- Display all the tables in the selected database
```
show collections
```

- Check the first few entries of a table (e.g. brtmsg)
```
db.brtmsg.find().limit(10)
```

- Select entry by a field
```
db.strategy.find( {"name": "Htao_Tucson_us"} )
```

- Remove a field of an entry which matches a specific condition
```
db.strategy.update({"name":"L_I_Ftang_Bolvar_jp"}, {$unset: {"end":""}})
```

- Export database table to a json file
```
mongoexport -h url -d database -c table -o file.json
```