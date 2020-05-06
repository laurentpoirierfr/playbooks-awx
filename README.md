# playbooks-awx

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


```json
{
    "extra_vars": {
        "profil": "develop",
        "version": "0.0.2-SNAPSHOT"
    }
}
```