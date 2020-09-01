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



