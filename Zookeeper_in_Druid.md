## Druid 에서 사용하는 Zookeeper
Druid 에서 사용되는 다양한 정보들을 Zookeeper 에 보관한다.
Task, Indexer 의 status, segment 정보 등..

## Zookeeper Tree

zkCli $> ls /druid/indexer
zkCli $> ls /druid/indexer/task
zkCli $> ls /druid/indexer/status/${hostname}:${MiddleManager Port}
zkCli $> get /druid/indexer/leaderLatchPath/${hash number}
zkCli $> get /druid/announcements
zkCli $> ls /druid/servedSegments
zkCli $> ls /druid/coordinator
zkCli $> ls /druid/segment
zkCli $> ls /druid/loadQueue
