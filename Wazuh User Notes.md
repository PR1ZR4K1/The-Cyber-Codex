2024/12/13 16:17
Status: #idea
Tags:

# Wazuh User Notes


| Username     | Password           | Hash                                                         |
| ------------ | ------------------ | ------------------------------------------------------------ |
| jaylon       | N0tMyJaylon!       | $2y$12$ulAPDbBqf5mm.6iwbFTmHuBJPz7/KhirY6n1KOHSSBmH4v559prvG |
| christian    | N0tMyChristian!    | $2y$12$WY42./24A8fa3MDqgzktb.v2alOghyKZkm/Viceo6fkxaR5kPFjwe |
| alberto      | N0tMyAlberto!      | $2y$12$JwYIJUjx217KbKZCr6grDO7T4NwdZsaxERFWkBN7NXWtCL/BoG.Tu |
| jess         | N0tMyJess!         | $2y$12$tLnvNgPOvZcq2kP7xqxEO.nEQpABwAUL40kob3C1klcZ3fcqKB0R. |
| maddie       | N0tMyMaddie!       | $2y$12$Inxw/lKbF4TcfnAX5sjIE./RQJ.bQqtzrsfDxfRH7sLcvHfZbgjZe |
| nate         | N0tMyNate!         | $2y$12$q8xKj1rD6GzwiQ97BQe5QucW4wCszvJS8.fyNwQM6F2IxIBepYmNi |
| brett        | N0tMyBrett!        | $2y$12$w3opeezDSVTXgxoq2oTbEe6JoJZS0QcuTKDqGJaYAscglFrXJewtq |
| nick         | N0tMyNick!         | $2y$12$e.Yt.5WUVPZrufFhHlZMr.HDXotk7ezr26CkIN6h1nUWzYb29agyO |
| kibanaserver | N0tMyKibanaServer! | $2y$12$sURxX.kCfSNh8hNmZYfXF.M5JNRHpaUvR9aqYexQFahQX7MBmy4hO |
| admin        | N0tMyAdmin!        | $2y$12$wz1ER52o9Q3D68/Rp1DTUOJQ9FN9jpJN6SmRwXOtJuvY9AdfkcWnW |
| wazuh-wui    | N0tMyWazuhWui!     |                                                              |

## Wazuh Create User Notes

Add users to internal_users.yml

```
## Custom users

  


jaylon:

hash: "$2y$12$ulAPDbBqf5mm.6iwbFTmHuBJPz7/KhirY6n1KOHSSBmH4v559prvG"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based jaylon user"

  
  

christian:

hash: "$2y$12$WY42./24A8fa3MDqgzktb.v2alOghyKZkm/Viceo6fkxaR5kPFjwe"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based christian user"

  
  

alberto:

hash: "$2y$12$JwYIJUjx217KbKZCr6grDO7T4NwdZsaxERFWkBN7NXWtCL/BoG.Tu"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based alberto user"

  
  

jess:

hash: "$2y$12$tLnvNgPOvZcq2kP7xqxEO.nEQpABwAUL40kob3C1klcZ3fcqKB0R."

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based jess user"

  
  

maddie:

hash: "$2y$12$Inxw/lKbF4TcfnAX5sjIE./RQJ.bQqtzrsfDxfRH7sLcvHfZbgjZe"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based maddie user"

  
  

nate:

hash: "$2y$12$q8xKj1rD6GzwiQ97BQe5QucW4wCszvJS8.fyNwQM6F2IxIBepYmNi"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based nate user"

  
  

brett:

hash: "$2y$12$w3opeezDSVTXgxoq2oTbEe6JoJZS0QcuTKDqGJaYAscglFrXJewtq"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based brett user"

  
  

nick:

hash: "$2y$12$e.Yt.5WUVPZrufFhHlZMr.HDXotk7ezr26CkIN6h1nUWzYb29agyO"

reserved: true

backend_roles:

- "all_access"

- "admin"

description: "Based nick user"
```

*Stop Containers*

```
docker compose down
```

**Change occurrences of old password with new ones in docker compose file**

### Start Containers!

**Exec into indexer container to apply changes**

```
docker exec -it single-node-wazuh.indexer-1 bash
```

**Set these**

```
export INSTALLATION_DIR=/usr/share/wazuh-indexer
CACERT=$INSTALLATION_DIR/certs/root-ca.pem
KEY=$INSTALLATION_DIR/certs/admin-key.pem
CERT=$INSTALLATION_DIR/certs/admin.pem
export JAVA_HOME=/usr/share/wazuh-indexer/jdk
```

**Run This**

```
bash /usr/share/wazuh-indexer/plugins/opensearch-security/tools/securityadmin.sh -cd /usr/share/wazuh-indexer/opensearch-security/ -nhnv -cacert  $CACERT -cert $CERT -key $KEY -p 9200 -icl
```

**Change in wazuh.yml in single-node/config/wazuh_dashboard dir**

```
run_as: true
```


**Update docker-compose.yml, config/wazuh_indexer/internal_users.yml, config/wazuh_dashboard/wazuh.yml for final repo**


---
# References
