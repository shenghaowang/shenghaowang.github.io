---
layout: page
title: psql
permalink: /notes/command-library/psql/
---

- Visit existing database
```bash
psql -d <db-name>
```
e.g. On dtlprod4, run `psql -d data`. This will work when the user and password to this db are both data_oper.

e.g. On mlu, access the syncing job database by `psql -d access_mgr -h s8.dtl -p 5436 -U access_mgr`. Password: access_mgrs

- Display all existing schemas
```
selet * from <space>
```
Press Tab on the keyboard.

* Create a schema in the database
```
create schema <schema_name>;
```

- Create table
```
create table tl.idea_ticker (
 idea_id varchar(20) PRIMARY KEY,
 bticker varchar(40)
);
```

- Update column under condition
```
update table
set column1 = value1,
    column2 = value2 ,...
where
 condition;
```

- Display columns of a table
```
\d <schema_name.table_name>
```

- Edit the type of a column
```
ALTER TABLE <tb_name> ALTER COLUMN <col_name> TYPE <new_type>;
```

- Delete data entry
```
delete from <tb-name> where <field=xxx>
```

- Quit database
```
\q
```

- Search for a database record by condition
```
db.strategy.find({"name":"Niagara"})
```

- Update a specific filed of a db record
```
db.strategy.update({"_id":166}, {$set: {"end": "20181211"}})
```

- Access alphastore database
```
trd_oper@dtlprod10:~/work/alphastore/mapping/alpha/new/property> psql -d alphastore -h dtlprod4 -p 9098
alphastore=# select * from alpha_property where region='jp' and id=43934;
```

- Access Bloomberg database

```bash
data_oper@dtlprod4:~> psql -dmain -hgold -U data_oper
Enter password: mulan76
main=> select * from bb.sec_map limit 5;
main=> select * from bb.sec_map where bsid = 'EQ0013577500001000';
main=> select * from mk.sec_list2 where id = 179021;

data_oper@dtlprod4:~> psql -U data_oper -h grv-wn -d main
Enter password: mulan76

psql -U super_query -h grv-wn -d main
Enter password: superqueryqqq
```