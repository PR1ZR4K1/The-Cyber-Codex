 2024/10/11 15:02
Status: #idea
Tags:

# Database Security Playbook

## I. General Database Security Principles

## II. MySQL/MariaDB

### A. Client Installation

1. Linux (try your package manag er and search for this)

*mysql-server*

Example:
```
sudo apt install mysql-server
```

2. Linux/Windows (Link)
```
http://dev.mysql.com/downloads/shell/
```

### B. Config/Log File Locations

**Generally stored here:**

*Linux*
```bash
/etc/mysql/my.cnf
/var/lib/mysql
```

*Windows*
```
- Default system-wide installation under `C:\ProgramData\MySQL\MySQL Router` : `C:\ProgramData\MySQL\MySQL Router\mysqlrouter.conf`
    
- In addition: ``C:\Users\_`username`_\AppData\Roaming\mysqlrouter.conf`` where _`username`_ is replaced with your system's user.
    
- In addition to _mysqlrouter.conf_, for backwards compatibility the system also looks for _mysqlrouter.ini_
```
### C. Connecting to Server

1. MySQL

```bash
mysql -h host -u user -p
```

2. MariaDB

```bash
mariadb -u root -p -h localhost
```

*Where -u specifies user, -p specifies you will input a  password, and -h specifies the hostname or ip*

### D. User Security

**Make sure every user has a password enabled and that they cannot be accessed without a password**

#### Create and Alter Users

```sql
CREATE USER 'bobby'@'localhost' IDENTIFIED BY '_password_';

ALTER USER 'bobby'@'localhost' IDENTIFIED BY '_password_';
```

#### Delete Users

```sql
DROP USER 'bobby'@'localhost';
```
### E. Data Encryption
**Prior to MySQL 8.0.16, data-at-rest is not encrypted!**

1. MySQL
#### Table-Level Encryption
```sql
-- Enable encryption for a specific table
CREATE TABLE encrypted_table (
    id INT PRIMARY KEY,
    data VARCHAR(100)
) ENCRYPTION='Y';

-- Alter existing table to enable encryption
ALTER TABLE existing_table ENCRYPTION='Y';

-- Check encryption status
SELECT TABLE_SCHEMA, TABLE_NAME, CREATE_OPTIONS 
FROM INFORMATION_SCHEMA.TABLES 
WHERE CREATE_OPTIONS LIKE '%ENCRYPTION%';
```

#### Global Encryption Settings
```sql
-- Set default encryption for all new tables
SET GLOBAL table_encryption_privilege_check=ON;
SET GLOBAL default_table_encryption=ON;

-- Configure keyring (required for encryption)
-- In my.cnf:
[mysqld]
early-plugin-load="keyring_file.so"
keyring_file_data="/var/lib/mysql-keyring/keyring"

-- Verify keyring status
SHOW PLUGINS WHERE Name LIKE 'keyring%';
```

#### Master Key Rotation
```sql
-- Rotate master key
ALTER INSTANCE ROTATE INNODB MASTER KEY;
```

2. MariaDB
#### File Key Management
```sql
-- Enable encryption plugin in my.cnf/server.cnf
[mysqld]
plugin_load_add = file_key_management
file_key_management_filename = /etc/mysql/encryption/keyfile
file_key_management_filekey = FILE:/etc/mysql/encryption/keyfile.key

-- Create encryption keys file (keyfile)
1;PATH_TO_KEY_1
2;PATH_TO_KEY_2
```

#### Table Encryption
```sql
-- Create encrypted table
CREATE TABLE encrypted_table (
    id INT PRIMARY KEY,
    data VARCHAR(100)
) ENCRYPTED=YES ENCRYPTION_KEY_ID=1;

-- Alter existing table
ALTER TABLE existing_table ENCRYPTED=YES ENCRYPTION_KEY_ID=1;

-- Check encryption status
SELECT TABLE_SCHEMA, TABLE_NAME, ENCRYPTION 
FROM INFORMATION_SCHEMA.TABLES 
WHERE ENCRYPTION='YES';
```

#### System-Wide Encryption
```sql
-- In my.cnf/server.cnf
[mysqld]
encrypt_binlog=1
encrypt_tmp_files=1
aria_encrypt_tables=1
encrypt_tmp_disk_tables=1
encrypt_tables=1

-- Verify encryption settings
SHOW VARIABLES LIKE '%encrypt%';
```

#### Key Rotation
```sql
-- Generate new encryption key
FILE_KEY_MANAGEMENT_GENERATE_KEY=1;

-- Rotate keys for specific table
ALTER TABLE table_name ENCRYPTION_KEY_ID=2;
```

#### Encryption Status and Monitoring
```sql
-- Check encryption status
SELECT * FROM information_schema.INNODB_TABLESPACES_ENCRYPTION;

-- Monitor encryption progress
SELECT * FROM information_schema.INNODB_ENCRYPTION_STATUS;
```

#### Backup Encryption
```sql
-- Enable encrypted backups
-- For mysqldump:
mysqldump --encrypt-protocol --ssl-ca=/path/to/ca.pem \
          --ssl-cert=/path/to/client-cert.pem \
          --ssl-key=/path/to/client-key.pem \
          -u username -p database > backup.sql

-- For Mariabackup:
mariabackup --encrypt=AES256 \
            --encrypt-key='encryption_key' \
            --backup \
            --target-dir=/backup/path
```

**Important Security Notes:**
1. Always store encryption keys separately from data
2. Implement key rotation policies
3. Backup encryption keys securely
4. Monitor encryption status regularly
5. Use SSL/TLS for data-in-transit encryption
6. Consider implementing disk-level encryption as additional security layer

This implementation provides comprehensive encryption at rest for both MySQL and MariaDB, covering table-level, system-wide, and backup encryption options.
#### References 

1. MySQL
```
Table encryption 
https://dev.mysql.com/doc/refman/8.0/en/innodb-data-encryption.html#innodb-data-encryption-enabling-disabling

global encryption
https://dev.mysql.com/doc/refman/8.0/en/innodb-data-encryption.html#innodb-schema-tablespace-encryption-default
```
2. MariaDB
```
file location for encryption variable definitions
https://mariadb.com/kb/en/aria-encryption-overview/

encryption plugin, key encryption and generation
https://mariadb.com/kb/en/file-key-management-encryption-plugin/
```

### F. Active Connections

**Tracking active connections can help us to potentially identify unknown users that may be malicious.**

```sql
SHOW PROCESSLIST;
```

*This command provides a list of active connections, including the user, host, database, and command being executed. You can use this command to monitor the current load on your MySQL server.*

```sql
SHOW STATUS LIKE 'Threads_connected';
```

*This will display a single row with the value of `Threads_connected` which indicates the number of currently open connections.*

```bash
mysqladmin -u root -p -i 5 extended-status | grep "Threads_connected"

mariadb-admin --extended-status | grep threads_connected
```

*One liner to view the number of active connections in real time every 5 seconds*

## III. PostgreSQL

### A. Client Installation
1. Linux (via package manager)
*postgresql*
Example:
```bash
sudo apt install postgresql postgresql-contrib
```

2. Linux/Windows (Official Download)
```
https://www.postgresql.org/download/
```

### B. Config/Log File Locations
**Generally stored here:**
*Linux*
```bash
/etc/postgresql/[version]/main/postgresql.conf    # Main configuration file
/var/lib/postgresql/[version]/main/              # Data directory
/var/log/postgresql/                             # Log files
```
*Windows*
```
C:\Program Files\PostgreSQL\[version]\data\postgresql.conf    # Main configuration file
C:\Program Files\PostgreSQL\[version]\data\                  # Data directory
```

### C. Connecting to Server
```bash
psql -h host -U username -d database
```
*Where -h specifies host, -U specifies user, and -d specifies database name. You'll be prompted for password.*

### D. User Security
**Ensure proper user authentication and access control**
#### Create and Alter Users
```sql
CREATE USER bobby WITH PASSWORD 'password';
ALTER USER bobby WITH PASSWORD 'new_password';
```

#### Delete Users
```sql
DROP USER bobby;
```

### E. Data Encryption
**PostgreSQL provides several layers of encryption:**

1. Connection Encryption (SSL/TLS)
```sql
-- Check SSL status
SHOW ssl;

-- Configure in postgresql.conf:
ssl = on
ssl_cert_file = 'server.crt'
ssl_key_file = 'server.key'
```

2. Data-at-rest Encryption
```
# File system level encryption options:
1. Full disk encryption
2. pgcrypto extension for column-level encryption:
```
```sql
-- Enable pgcrypto extension
CREATE EXTENSION pgcrypto;

-- Example of encrypting data
INSERT INTO table_name (encrypted_column) 
VALUES (pgp_sym_encrypt('secret data', 'encryption_key'));
```

### F. Active Connections
**Monitor active connections for security:**

```sql
-- View all active connections
SELECT * FROM pg_stat_activity;

-- Count of active connections
SELECT count(*) FROM pg_stat_activity WHERE state = 'active';

-- View connected users and their activity
SELECT usename, client_addr, client_port, 
       state, query_start, query 
FROM pg_stat_activity;

-- Kill a specific connection
SELECT pg_terminate_backend(pid);
```

One-liner to monitor connections in real-time:
```bash
watch -n 5 "psql -U postgres -c 'SELECT count(*) FROM pg_stat_activity;'"
```
## IV. Microsoft SQL Server

### A. Installation and Configuration

1. Use SQL Server Configuration Manager to:
- Enable only necessary protocols
- Configure SQL Server services to run under low-privilege accounts

2. Enable SQL Server Audit:
```sql
CREATE SERVER AUDIT Audit_Name
TO FILE (FILEPATH = 'C:\audit\');
```

### B. User Management

1. Create login and user with least privileges:
```sql
CREATE LOGIN username WITH PASSWORD = 'password';
CREATE USER username FOR LOGIN username;
GRANT SELECT, INSERT, UPDATE ON schema_name.table_name TO username;
```

2. Implement contained database users:
```sql
CREATE USER username WITH PASSWORD = 'password';
```

### C. Data Encryption

1. Enable Transparent Data Encryption (TDE):
```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'complex!password123';
CREATE CERTIFICATE TDECert WITH SUBJECT = 'TDE Certificate';
CREATE DATABASE ENCRYPTION KEY WITH ALGORITHM = AES_256 ENCRYPTION BY SERVER CERTIFICATE TDECert;
ALTER DATABASE database_name SET ENCRYPTION ON;
```

## V. Oracle Database

### A. Installation and Configuration

1. Use Oracle Net Configuration Assistant to configure listener securely

2. Enable auditing in init.ora:
```
AUDIT_TRAIL = DB,EXTENDED
```

### B. User Management

1. Create user with least privileges:
```sql
CREATE USER username IDENTIFIED BY password;
GRANT CREATE SESSION TO username;
GRANT SELECT, INSERT, UPDATE ON schema.table_name TO username;
```

2. Implement Oracle Virtual Private Database (VPD):
```sql
CREATE OR REPLACE FUNCTION auth_orders(
  schema_var IN VARCHAR2,
  table_var IN VARCHAR2
)
RETURN VARCHAR2
IS
BEGIN
 RETURN 'SALES_REP_ID = SYS_CONTEXT(''USERENV'', ''SESSION_USER'')';
END auth_orders;
/

BEGIN
DBMS_RLS.ADD_POLICY (
  object_schema   => 'sales',
  object_name     => 'orders',
  policy_name     => 'orders_policy',
  function_schema => 'sales',
  policy_function => 'auth_orders',
  statement_types => 'SELECT, INSERT, UPDATE, DELETE'
);
END;
/
```

### C. Data Encryption

1. Implement Transparent Data Encryption (TDE):
```sql
ALTER SYSTEM SET ENCRYPTION KEY IDENTIFIED BY "password";
ALTER TABLE schema.table_name ENCRYPT;
```

## VI. MongoDB

### A. Installation and Configuration

1. Enable authentication in mongod.conf:
```yaml
security:
 authorization: enabled
```

2. Use TLS/SSL for client connections:
```yaml
net:
 ssl:
   mode: requireSSL
   PEMKeyFile: /path/to/mongodb.pem
```

### B. User Management

1. Create user with specific roles:
```javascript
db.createUser(
 {
   user: "username",
   pwd: "password",
   roles: [ { role: "readWrite", db: "database_name" } ]
 }
)
```

2. Implement role-based access control:
```javascript
db.createRole(
 {
   role: "readOnlyRole",
   privileges: [
	 { resource: { db: "database_name", collection: "" }, actions: [ "find" ] }
   ],
   roles: []
 }
)
```

### C. Data Encryption

1. Enable encryption at rest:
```yaml
security:
 enableEncryption: true
 encryptionKeyFile: /path/to/keyfile
```

2. Use client-side field level encryption:
```javascript
const clientSideFieldLevelEncryptionOptions = {
 keyVaultNamespace: "encryption.__keyVault",
 kmsProviders: {
   local: {
	 key: localMasterKey
   }
 }
};
```

## VII. Common Security Practices

1. Regular patching: $Vulnerability\_Risk \propto \frac{1}{Patch\_Frequency}$
2. Backup strategy: $Recovery\_Time\_Objective < Maximum\_Tolerable\_Downtime$
3. Network segmentation: Implement $VLAN\_Isolation$ and $Firewall\_Rules$
4. Monitoring and alerting: $Alert\_Threshold = \mu + k\sigma$ where $\mu$ is the mean and $\sigma$ is the standard deviation of normal behavior
5. Penetration testing: Conduct tests at intervals of $t = \frac{1}{Risk\_Level}$

Remember to adapt these practices to your specific environment and risk profile. Regular review and updates to this playbook are crucial for maintaining robust database security.





---
# References