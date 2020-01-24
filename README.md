# av_herzogenbuchsee_los5

```
docker run --rm --name edit-db -p 54321:5432 --hostname primary \
-e PG_DATABASE=edit -e PG_LOCALE=de_CH.UTF-8 -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary \
-e PG_USER=admin -e PG_PASSWORD=admin \
-e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl \
-e PG_ROOT_PASSWORD=secret \
-e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl \
-e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server \
sogis/oereb-db:latest
```


```
java -jar /Users/stefan/apps/ili2pg-4.3.2/ili2pg-4.3.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin \
--dbschema av_herzogenbuchsee --models DM01AVBE11LV95D \
--defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createEnumTabs \
--createMetaInfo --createUnique --createNumChecks --nameByTopic \
--createTidCol \
--schemaimport

java -jar /Users/stefan/apps/ili2pg-4.3.2/ili2pg-4.3.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin \
--dbschema av_herzogenbuchsee --models DM01AVBE11LV95D \
--defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createEnumTabs \
--createMetaInfo --createUnique --createNumChecks --nameByTopic \
--createTidCol \
--disableValidation \
--import 0979000005.ITF 



java -jar /Users/stefan/apps/ili2pg-4.3.2/ili2pg-4.3.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin \
--dbschema av_herzogenbuchsee --models DM01AVBE11LV95D \
--defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createEnumTabs \
--createMetaInfo --createUnique --createNumChecks --nameByTopic \
--createTidCol \
--disableValidation \
--doSchemaImport \
--import 0979000005.ITF 
```


```
DROP TABLE av_herzogenbuchsee.t_perimeter;

CREATE TABLE av_herzogenbuchsee.t_perimeter (
    id int GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
    geometrie geometry(POLYGON, 2056) NOT NULL
);

ALTER TABLE av_herzogenbuchsee.t_perimeter OWNER TO "admin";
GRANT ALL ON TABLE av_herzogenbuchsee.t_perimeter TO "admin";
```

```
insert into geom from text...
```