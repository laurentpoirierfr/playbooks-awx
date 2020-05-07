# playbooks-awx

### Ré&férences 

* https://github.com/ansible/awx
* https://docs.ansible.com/ansible-tower/latest/html/towerapi/api_ref.html#/
* https://docs.ansible.com/ansible-tower/latest/html/userguide/job_templates.html


### Liste des api :

```bash
curl -u admin:password -X GET http://localhost:8080/api/v2/ | jq
```

### Liste des jobs

```bash
curl -u admin:password -X GET http://localhost:8080/api/v2/jobs/ | jq
```

### Mon job_template


```bash
curl -u admin:password -X GET http://localhost:8080/api/v2/job_templates/ | jq

curl -u admin:password -X GET http://localhost:8080/api/v2/job_templates/11/ | jq

curl -u admin:password -X POST http://localhost:8080/api/v2/job_templates/11/launch/ \
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
curl -u admin:password -X GET http://localhost:8080/api/v2/inventories/ | jq
```

