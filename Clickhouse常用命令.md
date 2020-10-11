

### 执行计划
```
EXPLAIN select sumMerge(pv) from ad.strategy_view where date=20200916
```
```
clickhouse-client --host 127.0.0.1 --port 9090 --send_logs_level=trace --query 'select sumMerge(pv) from ad where date=20200916 '
```
