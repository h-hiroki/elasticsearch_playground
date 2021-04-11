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
curl http://localhost:9200/_nodes/plugins?pretty
```

インデックス作成
```sh
curl -X PUT http://localhost:9200/houses/
```

インデックス確認
```sh
curl http://localhost:9200/houses/?pretty
```

ドキュメント追加
```sh
# Typeは使わなくなりました。typeの箇所は_docに変えます。
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_doc/1?pretty -d @assets/data/houses/document1.json
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_doc/2?pretty -d @assets/data/houses/document2.json
```

ドキュメント検索
```sh
# 名前で検索
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_search?pretty -d '
{
    "query": {
        "match": {
            "name": "カイバヒルズ"
        }
    }
}
'

# And検索
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_search?pretty -d '
{
    "query": {
        "bool": {
            "must": [
                {
                    "match": {
                        "name": "カイバヒルズ"
                    }
                },
                {
                    "match": {
                        "description": "夜景"
                    }
                }
            ]
        }
    }
}
'

# Or検索
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_search?pretty -d '
{
    "query": {
        "bool": {
            "should": [
                {
                    "match": {
                        "name": "カイバヒルズ"
                    }
                },
                {
                    "match": {
                        "description": "夜景"
                    }
                }
            ]
        }
    }
}
'

# ソート
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_search?pretty -d '
{
    "sort": [
        {
            "stations.minutes_on_foot": "desc"
        }
    ]
}
'

# 範囲指定
curl -X POST -H "Content-Type: application/json" http://localhost:9200/houses/_search?pretty -d '
{
    "query": {
        "range": {
            "stations.minutes_on_foot": {
                "lte": 2
            }
        }
    }
}
'
```
