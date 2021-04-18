# impress

# env
- Elasticsearch: `7.6.2`
- Kibana: `7.6.2`

# Document operation
## CRUD
### Create

```sh
curl -XPUT "http://localhost:9200/my_index/_doc/1" -H 'Content-Type: application/json' -d'{  "user_name": "John Smith",  "date": "2019-01-06T15:09:45",  "message": "Hello Elasticsearch world."}'
```

```sh
curl -XPOST "http://localhost:9200/my_index/_doc" -H 'Content-Type: application/json' -d'{  "user_name": "John Smith",  "date": "2019-01-06T15:09:45",  "message": "Hello Elasticsearch world."}'
```