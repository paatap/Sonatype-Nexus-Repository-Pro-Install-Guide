# Sonatype-Nexus-Repository-Pro-Install-Guide


**Move Postgres DB To /opt folder**

cd dir

mkdir /pgsql13

cd pgsql13

mkdir data

chown -R postgres:postgres /opt/pgsql13/

cat  /usr/lib/systemd/system/postgresql-13.service

edit this file

**change path to pgdata**

_> # Location of database directory
Environment=PGDATA=/opt/pgsql13/data/


/usr/pgsql-13/bin/postgresql-13-setup initdb

systemctl enable postgresql-13

systemctl start postgresql-13

systemctl enable postgresql.service


**Postgres 13 connection issue via SSL antentification**

**Add this  lines to pg_hba.conf**

-> # host  all     all 0.0.0.0/0 md5
host    all             all             10.91.206.88/32         md5
host    all             all             0.0.0.0/0               trust



**True instuction on this link**

**Do not upload lic file via curl- do not works -Bug Upload via Web Interface**

https://help.sonatype.com/repomanager3/installation-and-upgrades/migrating-to-a-new-database

**Migration**

cd /opt/sonatype-work/nexus3/etc/fabric
 
java -Xmx4G -Xms4G -XX:MaxDirectMemorySize=4014M -jar nexus-db-migrator-3.39.0-01.jar --migration_type=postgres --db_url="jdbc:postgresql://10.91.209.209:5432/nexus?user=nexus&password=nexus"


**Connect To Postgres**

cd  /nexus v-/etc 

touch nexus.properties
echo "nexus.datastore.enabled=true" >> nexus.properties

echo "nexus.heartbeat.enabled=true >> nexus.properties

echo "nexus.heartbeat.interval=600 >> nexus.properties

echo "nexus.heartbeat.history=30 >> nexus.properties

echo "username=nexus password=nexus >> nexus.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus >> nexus.properties

echo "advanced=maximumPoolSize\=200 >> nexus.properties


echo "nexus.hazelcast.discovery.isEnabled=true" >> nexus-default.properties

![Screenshot from 2022-06-24 14-21-51](https://user-images.githubusercontent.com/16716538/175542528-a170c61e-c647-4146-a427-a8f244f6eaec.png)

![Screenshot from 2022-06-24 14-22-12](https://user-images.githubusercontent.com/16716538/175543274-1c52547b-42b3-4e4c-b655-989bd44404d7.png)

mkdir fabric


touch(if not exist) nexus-store.properties

echo "nexus.datastore.enabled.true" >> nexus-store.properties

echo "username=nexus password=nexus" >> nexus-store.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus-store.properties

echo "advanced=maximumPoolSize\=200" >> nexus-store.properties





cd /nexus...-work/nexus3/etc

touch(if not exist) nexus.properties


echo "nexus.datastore.enabled=true" >> nexus.properties

echo "nexus.heartbeat.enabled=true" >> nexus.properties

echo "nexus.heartbeat.interval=600" >> nexus.properties

echo "nexus.heartbeat.history=30" >> nexus.properties

echo "username=nexus" >> nexus.properties

echo "password=nexus" >> nexus.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus.properties

echo "advanced=maximumPoolSize\=200" >> nexus.properties

mkdir fabric


touch(if not exist) nexus-store.properties



echo "password=nexus" >> nexus-store.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus-store.properties

echo "username=nexus" >> nexus-store.properties

echo "advanced=maximumPoolSize\=200" >> nexus-store.properties




./nexus run (to trace)   (./nexus start/stop/restart)  
