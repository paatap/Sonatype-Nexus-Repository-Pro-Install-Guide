# Sonatype-Nexus-Repository-Pro-Install-Guide




Postgres 13 connection issu via SSL antentification

Add this  lines to pg_hba.conf

-> # host  all     all 0.0.0.0/0 md5
host    all             all             10.91.206.88/32         md5
host    all             all             0.0.0.0/0               trust



True instuction on this link

https://help.sonatype.com/repomanager3/installation-and-upgrades/migrating-to-a-new-database

Migration

cd /opt/sonatype-work/nexus3/etc/fabric
 
java -Xmx4G -Xms4G -XX:MaxDirectMemorySize=4014M -jar nexus-db-migrator-3.39.0-01.jar --migration_type=postgres --db_url="jdbc:postgresql://10.91.209.209:5432/nexus?user=nexus&password=nexus"


Connect To Postgres

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
