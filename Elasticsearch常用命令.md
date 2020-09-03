### 查看集群状态

```
GET _cluster/health
GET _cluster/health?level=indices
GET _cat/indices?v&health=red
GET _cluster/allocation/explain
```

### 清除节点上的缓存
```
POST /_cache/clear
```

### 查询模板
```
GET _template
```

### 设置默认模板
```
PUT _template/template_default
{
  "order": 2,
  "version": 1,
  "index_patterns": [
    "*"
  ],
  "settings": {
    "index": {
      "number_of_shards": "3",
      "number_of_replicas": "1",
      "refresh_interval": "30s"
    }
  },
  "mappings": {},
  "aliases": {}
}
```

### 增加默认模板
```
PUT _template/template_log
{
    "order": 0,
    "version": 1,
    "index_patterns": [
        "log*"
    ],
    "mappings": {
        "doc": {
            "dynamic": "false",
            "properties": {
                "Status": {
                    "type": "keyword"
                },
                "Runtime": {
                    "type": "float"
                },
                "request_length": {
                    "type": "integer"
                },
                "request_time": {
                    "type": "float"
                },
                "status": {
                    "type": "integer"
                },
                "upstream_response_time": {
                    "type": "float"
                },
                "type": {
                    "type": "keyword"
                }
            }
        }
    }
}
```

### 设置刷新时间
```
PUT book-v1/_settings
{
    "index" : {
        "refresh_interval" : "1s"
    }
}
```

### 删除具体doc
```
DELETE {index}/doc/{id}
```

### 查询条数
```
GET {index}/orders/_count
```

### reindex
```
POST _reindex
{
  "conflicts": "proceed",
  "source": {
    "index": "book-v1"
  },
  "dest": {
    "index": "book-v2",
    "op_type": "create"
  }
}
```
### 批量修改
```
POST _bulk
{"update":{"_index":"book-v4","_type":"orders","_id":1}}
{"doc":{"traits":["纯色","纯色"]}}
```

###  search
```
GET book-v4/orders/_search
{
  "size": 0,
  "aggs": {
    "user_info": {
      "terms": {
        "field": "user_id",
        "size": 200
      },
      "aggs": {
        "count_class": {
          "cardinality": {
            "field": "class"
          }
        },
        "count_department": {
          "cardinality": {
            "field": "department"
          }
        }
      }
    }
  }
}

```


