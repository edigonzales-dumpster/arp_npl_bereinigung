# arp_npl_bereinigung

## Database
```
docker run --rm --name edit-db -p 64321:5432 --hostname primary -e PG_DATABASE=edit -e PG_LOCALE=de_CH.UTF-8 -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary -e PG_USER=admin -e PG_PASSWORD=admin -e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl -e PG_ROOT_PASSWORD=secret -e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl -e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server -v ~/pgdata-npl:/pgdata:delegated sogis/oereb-db:latest
```

Vorhandene `arp_npl.sql`  und `arp_npl_pub.sql` verwenden für Edit- und Pub-DB (wobei es hier nur eine DB gibt.)

## GRETL
```
export ORG_GRADLE_PROJECT_dbUriEdit=jdbc:postgresql://localhost:64321/edit
export ORG_GRADLE_PROJECT_dbUserEdit=admin
export ORG_GRADLE_PROJECT_dbPwdEdit=admin
export ORG_GRADLE_PROJECT_dbUriPub=jdbc:postgresql://localhost:64321/edit
export ORG_GRADLE_PROJECT_dbUserPub=admin
export ORG_GRADLE_PROJECT_dbPwdPub=admin
export ORG_GRADLE_PROJECT_dbUriSogis=jdbc:postgresql://geodb.verw.root.sorg:5432/sogis
export ORG_GRADLE_PROJECT_dbUserSogis=bjsvwzie
export ORG_GRADLE_PROJECT_dbPwdSogis=fubar

```

```
./start-gretl.sh --docker-image sogis/gretl-runtime:latest  --job-directory $PWD/arp_npl_pub tasks --all
```

Container heisst gretl-npl (siehe `start-gretl.sh`) damit man andere GRETL-Prozesse auf dem gleichen Computer laufen lassen kann.

## Datenimport

```
java -jar 
```


