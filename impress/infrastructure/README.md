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

- PUTの場合IDを指定して登録される
- POSTの場合IDが自動採番される

### Read
```sh
curl -XGET "http://localhost:9200/my_index/_doc/1"
```

```sh
curl -XGET "http://localhost:9200/my_index/_source/1"
```

- _docを利用すると管理上のメタデータも取得する
- _sourceを利用すると自分で登録したデータのみ取得する
