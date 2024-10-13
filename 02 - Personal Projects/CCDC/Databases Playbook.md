2024/10/11 15:02
Status: #idea
Tags:

# Database Security Playbook

## I. General Database Security Principles

## II. MySQL/MariaDB

### A. Installation and Configuration

1. Secure installation:
   ```bash
   mysql_secure_installation
   ```

2. Configure my.cnf:

```ini
[mysqld]
bind-address = 127.0.0.1
local-infile = 0
```

### B. User Management

1. Create user with limited privileges:
```sql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT, INSERT, UPDATE ON database_name.* TO 'username'@'localhost';
```

2. Remove anonymous users:
```sql
DELETE FROM mysql.user WHERE User='';
```

### C. Data Encryption

1. Enable SSL:
```sql
ALTER USER 'username'@'localhost' REQUIRE SSL;
```

2. Implement at-rest encryption:
```sql
ALTER TABLE table_name ENCRYPTION='Y';
```

## III. PostgreSQL

### A. Installation and Configuration

1. Modify pg_hba.conf:
```
host    all    all    127.0.0.1/32    md5
```

2. Set password encryption in postgresql.conf:
```
password_encryption = scram-sha-256
```

### B. User Management

1. Create role with limited privileges:
```sql
CREATE ROLE username WITH LOGIN PASSWORD 'password';
GRANT SELECT, INSERT, UPDATE ON ALL TABLES IN SCHEMA public TO username;
```

2. Implement role-based access control:
```sql
CREATE ROLE readonly;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly;
GRANT readonly TO username;
```

### C. Data Encryption

1. Use pgcrypto for column-level encryption:
```sql
CREATE EXTENSION pgcrypto;
UPDATE users SET password = crypt('newpassword', gen_salt('bf'));
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