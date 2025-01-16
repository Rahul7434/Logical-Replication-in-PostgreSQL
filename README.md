# Logical-Replication-in-PostgreSQL

Logical replication allows selective data replication between postgresql database.It uses a publish-subscribe model.

#### Prerequisites
1. Logical replication support from postgresql 10 onwords. Soconfirm the version
   ```
   psql --version
   ```
2. The table to be replicated must have a primary key or a unique index.

3. Create a user with replication privileges.
   ```
   CREATE ROLE replicator WITH REPLICATION LOGIN PASSWORD 'your_password';
   ```
4. Update the following Parameters in the publisher server's postgresql.conf file.
   ```
   wal_level = logical
   max_replication_slots= 10
   max_wal_sender= 10

   # Restart Postgresql to Applay changes.

   systemctl restart postgresql
   ```
5. Add an entry to allow the subscriber to connect.
   ```
   host replication replicator <subscriber_ip/subnet> md5
   ```
---

