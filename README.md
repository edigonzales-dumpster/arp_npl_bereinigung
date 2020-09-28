# arp_npl_bereinigung

## Database
```
docker run --rm --name edit-db -p 64321:5432 --hostname primary -e PG_DATABASE=edit -e PG_LOCALE=de_CH.UTF-8 -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary -e PG_USER=admin -e PG_PASSWORD=admin -e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl -e PG_ROOT_PASSWORD=secret -e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl -e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server -v ~/pgdata-npl:/pgdata:delegated sogis/oereb-db:latest
```

Vorhandene `arp_npl.sql`  und `arp_npl_pub.sql` verwenden für Edit- und Pub-DB (wobei es hier nur eine DB gibt.)

## GRETL
```
export ORG_GRADLE_PROJECT_dbUriEdit=jdbc:postgresql://host.docker.internal:64321/edit
export ORG_GRADLE_PROJECT_dbUserEdit=admin
export ORG_GRADLE_PROJECT_dbPwdEdit=admin
export ORG_GRADLE_PROJECT_dbUriPub=jdbc:postgresql://host.docker.internal:64321/edit
export ORG_GRADLE_PROJECT_dbUserPub=admin
export ORG_GRADLE_PROJECT_dbPwdPub=admin
export ORG_GRADLE_PROJECT_dbUriSogis=jdbc:postgresql://geodb.verw.rootso.org:5432/sogis
export ORG_GRADLE_PROJECT_dbUserSogis=bjsvwzie
export ORG_GRADLE_PROJECT_dbPwdSogis=fubar


export ORG_GRADLE_PROJECT_dbUriEdit=jdbc:postgresql://localhost:64321/edit
export ORG_GRADLE_PROJECT_dbUserEdit=admin
export ORG_GRADLE_PROJECT_dbPwdEdit=admin
export ORG_GRADLE_PROJECT_dbUriPub=jdbc:postgresql://localhost:64321/edit
export ORG_GRADLE_PROJECT_dbUserPub=admin
export ORG_GRADLE_PROJECT_dbPwdPub=admin
export ORG_GRADLE_PROJECT_dbUriSogis=jdbc:postgresql://geodb.verw.rootso.org:5432/sogis
export ORG_GRADLE_PROJECT_dbUserSogis=bjsvwzie
export ORG_GRADLE_PROJECT_dbPwdSogis=fubar

```

```
./start-gretl.sh --docker-image sogis/gretl-runtime:latest --job-directory $PWD/arp_npl_pub tasks --all
```

Container heisst gretl-npl (siehe `start-gretl.sh`) damit man andere GRETL-Prozesse auf dem gleichen Computer laufen lassen kann.

## Datenimport / -export

```
java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2401 --import /Users/stefan/tmp/npl/2401.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2403 --import /Users/stefan/tmp/npl/2403.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2405 --import /Users/stefan/tmp/npl/2405.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2407 --import /Users/stefan/tmp/npl/2407.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2408 --import /Users/stefan/tmp/npl/2408.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2421 --import /Users/stefan/tmp/npl/2421.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2455 --import /Users/stefan/tmp/npl/2455.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2456 --import /Users/stefan/tmp/npl/2456.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2457 --import /Users/stefan/tmp/npl/2457.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2473 --import /Users/stefan/tmp/npl/2473.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2474 --import /Users/stefan/tmp/npl/2474.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2475 --import /Users/stefan/tmp/npl/2475.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2476 --import /Users/stefan/tmp/npl/2476.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2477 --import /Users/stefan/tmp/npl/2477.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2479 --import /Users/stefan/tmp/npl/2479.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2491 --import /Users/stefan/tmp/npl/2491.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2498 --import /Users/stefan/tmp/npl/2498.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2501 --import /Users/stefan/tmp/npl/2501.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2502 --import /Users/stefan/tmp/npl/2502.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2514 --import /Users/stefan/tmp/npl/2514.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2546 --import /Users/stefan/tmp/npl/2546.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2551 --import /Users/stefan/tmp/npl/2551.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2573 --import /Users/stefan/tmp/npl/2573.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2574 --import /Users/stefan/tmp/npl/2574.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2580 --import /Users/stefan/tmp/npl/2580.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2581 --import /Users/stefan/tmp/npl/2581.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2582 --import /Users/stefan/tmp/npl/2582.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2586 --import /Users/stefan/tmp/npl/2586.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2613 --import /Users/stefan/tmp/npl/2613.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2614 --import /Users/stefan/tmp/npl/2614.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2615 --import /Users/stefan/tmp/npl/2615.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2616 --import /Users/stefan/tmp/npl/2616.xtf

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableRounding --disableValidation --dataset 2617 --import /Users/stefan/tmp/npl/2617.xtf


```

...Datenumbau...

```
java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl_pub --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_Publikation_20190909  --disableRounding --disableValidation --export pub_export.xtf


```

## Daten löschen
```
java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2401 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2403 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2405 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2407 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2408 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2421 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2455 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2456 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2457 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2473 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2474 --delete

java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2475 --delete

```



## Resultate (ohne --disableRounding beim Import)

### 2401
```
Info: dumpObjHelper(): SELECT r0.T_Id, r0.T_Ili_Tid,r0.typ_bezeichnung,r0.typ_abkuerzung,r0.typ_verbindlichkeit,r0.typ_bemerkungen,r0.typ_kt,r0.typ_code_kommunal,ST_AsEWKB(r0.geometrie),r0.name_nummer,r0.rechtsstatus,r0.publiziert_ab,r0.bemerkungen,r0.erfasser,r0.datum_erfassung,cast(r0.dokumente as text),r0.bfs_nr FROM arp_npl_pub.nutzungsplanung_erschliessung_linienobjekt r0 (TransferToXtf.java:998)

java.lang.NumberFormatException
    java.math.BigDecimal.<init>(BigDecimal.java:497)
    java.math.BigDecimal.<init>(BigDecimal.java:383)
    java.math.BigDecimal.<init>(BigDecimal.java:809)
    ch.interlis.iox_j.validator.Validator.roundNumeric(Validator.java:4021)


c12e9a21-1567-4d56-9659-7399f6cc56f2

LINESTRING (2627194.315 1240627.109, 2627182.304 1240645.04, 2627174.303 1240657.065, 2627174.298 1240657.073, 2627169.213 1240664.639, 2627167.413 1240667.228, 2627167.337916184 1240667.3289622879, 2627167.256642205 1240667.4250117715, 2627167.169498692 1240667.5157695317, 2627167.076829429 1240667.6008775262, 2627166.979 1240667.68, 2627166.876293401 1240667.752893117, 2627166.769209178 1240667.819188074, 2627166.6581706135 1240667.878622821, 2627166.5436166185 1240667.9309624257, 2627166.426 1240667.976, 2627145.597 1240698.948, 2627145.581 1240698.972, 2627137.042 1240711.277, 2627137.0630391724 1240711.390998784, 2627137.0774417263 1240711.5060245895, 2627137.085159327 1240711.6216913874, 2627137.0861660726 1240711.7376109974, 2627137.080458586 1240711.8533943905, 2627137.0680560204 1240711.9686529948, 2627137.049 1240712.083, 2627137.0233275243 1240712.1961563057, 2627136.991139578 1240712.3076343827, 2627136.9525443856 1240712.4170594101, 2627136.907671715 1240712.5240634708, 2627136.856672441 1240712.6282867866, 2627136.7997180372 1240712.7293789298, 2627136.737 1240712.827, 2627131.24 1240720.856, NaN NaN, NaN NaN, 2627131.216 1240720.889, NaN NaN, NaN NaN, 2627131.192 1240720.922, 2627130.284 1240722.139, 2627122.12 1240734.111, 2627122.0490982416 1240734.2087009093, 2627121.9724271614 1240734.3019429194, 2627121.8902664883 1240734.3903858433, 2627121.80291598 1240734.4737070035, 2627121.710694329 1240734.5516024083, 2627121.613937999 1240734.6237878616, 2627121.513 1240734.69, 2627121.4081399124 1240734.7500552111, 2627121.2998419935 1240734.8036632992, 2627121.188502167 1240734.8506282796, 2627121.074527478 1240734.8907784543, 2627120.958334603 1240734.923967039, 2627120.840348329 1240734.9500727006, 2627120.721 1240734.969, 2627120.643 1240734.979, 2627102.534 1240761.341)

```

### 2403
i.O.

### 2405 
Wieder `java.lang.NumberFormatException`.


## Neuer Ansatz 

### Segmentierung durch DB
```
java -jar /usr/local/ili2pg-4.3.1/ili2pg.jar \
--dbschema arp_npl --models SO_Nutzungsplanung_20171118 \
--defaultSrsCode 2056 --createGeomIdx --createFk --createFkIdx --createEnumTabs --beautifyEnumDispName --createMetaInfo --createUnique --createNumChecks --nameByTopic \
--createBasketCol --createDatasetCol --createImportTabs \
--createscript arp_npl_arcs.sql
```

### Disable Rounding beim Import
```
java -jar /usr/local/ili2pg-4.3.1/ili2pg.jar \
--dbschema arp_npl --models SO_Nutzungsplanung_20171118 \
--defaultSrsCode 2056 --strokeArcs --disableRounding --createGeomIdx --createFk --createFkIdx --createEnumTabs --beautifyEnumDispName --createMetaInfo --createUnique --createNumChecks --nameByTopic \
--createBasketCol --createDatasetCol --createImportTabs \
--createscript arp_npl_no_rounding.sql
```

Hat anscheinend beim Schemaanlegen keinen Einfluss. Sondern nur beim Import.

```
java -jar /Users/stefan/apps/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 64321 --dbdatabase edit --dbschema arp_npl --dbusr admin --dbpwd admin --models SO_Nutzungsplanung_20171118 --disableValidation --dataset 2401 --disableRounding --import /Users/stefan/tmp/npl/2401.xtf

```
LINESTRING (2627194.315 1240627.109, 2627182.304 1240645.04, 2627174.303 1240657.065, 2627174.298 1240657.073, 2627169.213 1240664.639, 2627167.413 1240667.228, 2627167.33792821 1240667.3290581037, 2627167.2566455826 1240667.425191597, 2627167.169474337 1240667.5160193897, 2627167.076760034 1240667.6011814245, 2627166.9788702107 1240667.6803401038, 2627166.876192919 1240667.753181629, 2627166.7691351897 1240667.8194172438, 2627166.658121418 1240667.8787843783, 2627166.5435916833 1240667.9310476906, 2627166.426 1240667.976, 2627145.597 1240698.948, 2627145.581 1240698.972, 2627137.042 1240711.277, 2627137.0630718716 1240711.3910512757, 2627137.077497229 1240711.506132231, 2627137.0852275626 1240711.6218558638, 2627137.0862368755 1240711.7378330105, 2627137.0805217735 1240711.8536736548, 2627137.068101476 1240711.9689882395, 2627137.0490177507 1240712.0833889768, 2627137.0233347737 1240712.1964911516, 2627136.991138914 1240712.307914416, 2627136.9525384414 1240712.417284068, 2627136.907663165 1240712.5242323114, 2627136.856663994 1240712.6283994934, 2627136.799712432 1240712.729435313, 2627136.737 1240712.827, 2627131.24 1240720.856, 2627131.216338146 1240720.8892459243, 2627131.192 1240720.922, 2627130.284 1240722.139, 2627122.12 1240734.111, 2627122.0490395585 1240734.2087288569, 2627121.9723088127 1240734.301995712, 2627121.890087649 1240734.3904603606, 2627121.802675983 1240734.473800113, 2627121.7103926623 1240734.5517109747, 2627121.613574304 1240734.6239087537, 2627121.5125740697 1240734.690130097, 2627121.407760373 1240734.7501334522, 2627121.2995155375 1240734.8036999474, 2627121.1882344047 1240734.8506341903, 2627121.074322889 1240734.890764981, 2627120.9581965012 1240734.923945936, 2627120.8402788304 1240734.9500560227, 2627120.721 1240734.969, 2627120.643 1240734.979, 2627102.534 1240761.341)