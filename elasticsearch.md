elasticsearch
=============

Use Kibana to explore the index. 

Index stats

```
GET /{index_name}/_stats
```

Get a single document, where *\_id* is the document ID,

```
GET /{index_name}/_doc/{_id}
```

Get a random document

```
POST /{index_name}/_search
{
   "size": 1,
   "query": {
      "function_score": {
         "functions": [
            {
               "random_score": {
                  "seed": "12345"
               }
            }
         ]
      }
   }
}
```

Get Elasticsearch version and cluster stats

```
GET /
```

## Creating indices / mapping

Field types:

- `keyword`: ids, email addresses, PKs/FKs (search by exact value)
- `constant_keyword`: always the same value
- `text`: full text, passed through analyzer
