# playbooks-awx

### Références 

* https://github.com/ansible/awx
* https://docs.ansible.com/ansible-tower/latest/html/towerapi/api_ref.html#/
* https://docs.ansible.com/ansible-tower/latest/html/userguide/job_templates.html

Interfaçage avec gitlab

* https://baptiste.bouchereau.pro/tutorial/setup-awx-with-gitlab/


### Liste des api :

```bash
curl -u admin:password -X GET http://localhost:9999/api/v2/ | jq
```

### Liste des jobs

```bash
curl -u admin:password -X GET http://localhost:9999/api/v2/jobs/ | jq
```

### Mon job_template


```bash
curl -u admin:password -X GET http://localhost:9999/api/v2/job_templates/ | jq

curl -u admin:password -X GET http://localhost:9999/api/v2/job_templates/9/ | jq

curl -u admin:password -X POST http://localhost:9999/api/v2/job_templates/9/launch/ \
     --data @awx-config.json -H "Content-Type: application/json"  | jq
```

### Fichier awx-config.json

```json
{
    "inventory": 2,
    "extra_vars": {
        "profil": "develop",
        "version": "0.0.2-SNAPSHOT"
    }
}
```

### Liste des inventaires

```bash
curl -u admin:password -X GET http://localhost:9999/api/v2/inventories/ | jq
```





# Rabbitmq

curl -u guest:guest -X PUT http://localhost:15672/api/users/admin \
     --data  '{"password": "admin", "tags": "administrator"}' \
     -H "Content-Type: application/json"

curl -u guest:guest -X PUT http://localhost:15672/api/permissions/%2F/admin \
     --data '{"vhost": "develop", "configure": ".*", "write": ".*", "read": ".*"}' \
     -H "Content-Type: application/json"



curl -u guest:guest -X PUT http://localhost:15672/api/exchanges/%2F/my-new-exchange  -d'{"type":"topic","durable":true}' -H "content-type:application/json"

curl -u guest:guest -X PUT http://localhost:15672/api/vhosts/new_vhost -H "content-type:application/json" 


