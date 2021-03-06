# Sonatype-Nexus-Repository-Pro-Install-Guide


**Move Postgres DB To /opt folder**

cd /opt

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

![Screenshot from 2022-06-24 14-22-46](https://user-images.githubusercontent.com/16716538/175543542-325c6dee-6073-44f7-a02f-1be5c7678f5a.png)

**mkdir fabric**

![Screenshot from 2022-06-24 14-33-12](https://user-images.githubusercontent.com/16716538/175544090-51bbe598-b6ff-4224-842a-903fe85fc385.png)


touch(if not exist) nexus-store.properties

![Screenshot from 2022-06-24 14-33-41](https://user-images.githubusercontent.com/16716538/175544193-2861c118-e95f-4b82-a9de-5af27d6a245f.png)

echo "nexus.datastore.enabled.true" >> nexus-store.properties

echo "username=nexus password=nexus" >> nexus-store.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus-store.properties

echo "advanced=maximumPoolSize\=200" >> nexus-store.properties

![Screenshot from 2022-06-24 14-34-25](https://user-images.githubusercontent.com/16716538/175544494-f54fc9ba-015f-49ab-9564-057124799193.png)



**cd /nexus...-work/nexus3/etc**

touch(if not exist) nexus.properties

![Screenshot from 2022-06-24 14-39-12](https://user-images.githubusercontent.com/16716538/175544593-20211e82-fbb3-41e1-bdd5-854bb74422ef.png)



echo "nexus.datastore.enabled=true" >> nexus.properties

echo "nexus.heartbeat.enabled=true" >> nexus.properties

echo "nexus.heartbeat.interval=600" >> nexus.properties

echo "nexus.heartbeat.history=30" >> nexus.properties

echo "username=nexus" >> nexus.properties

echo "password=nexus" >> nexus.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus.properties

echo "advanced=maximumPoolSize\=200" >> nexus.properties

![Screenshot from 2022-06-24 14-41-07](https://user-images.githubusercontent.com/16716538/175544831-479da081-d50e-4683-a777-2c21c27c2954.png)


**mkdir fabric**


touch(if not exist) nexus-store.properties

![Screenshot from 2022-06-24 14-43-33](https://user-images.githubusercontent.com/16716538/175544923-9fb702da-9443-4f04-bf4b-4cab091c2e64.png)



echo "password=nexus" >> nexus-store.properties

echo "jdbcUrl=jdbc\:postgresql\://10.91.209.209\:5432/nexus" >> nexus-store.properties

echo "username=nexus" >> nexus-store.properties

echo "advanced=maximumPoolSize\=200" >> nexus-store.properties


![Screenshot from 2022-06-24 14-49-15](https://user-images.githubusercontent.com/16716538/175544998-b1b208a1-9173-41cc-8cb1-0195f2750a8d.png)



./nexus run (to trace)   (./nexus start/stop/restart)  
