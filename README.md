# elasticsearch_playground
遊び場！

## kibana
```
http://localhost:5601/
```

## any command for Elasticsearch

サーバ起動確認
```sh
curl http://localhost:9200
```

プラグイン確認
```sh
curl http://localhost:9200/_nodes/plugins\?pretty
```

インデックス作成
```sh
curl -X PUT http://localhost:9200/houses/
```

インデックス確認
```sh
curl http://localhost:9200/houses/\?pretty
```

