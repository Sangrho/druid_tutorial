## Druid 에서 사용하는 Zookeeper
Druid 에서 사용되는 다양한 정보들을 Zookeeper 에 보관한다.<br/>
Task, Indexer 의 status, segment 정보 등..<br/>

## Zookeeper Tree

zkCli $> ls /druid/indexer<br/>
zkCli $> ls /druid/indexer/task<br/>
zkCli $> ls /druid/indexer/status/${hostname}:${MiddleManager Port}<br/>
zkCli $> get /druid/indexer/leaderLatchPath/${hash number}<br/>
zkCli $> get /druid/announcements<br/>
zkCli $> ls /druid/servedSegments<br/>
zkCli $> ls /druid/coordinator<br/>
zkCli $> ls /druid/segment<br/>
zkCli $> ls /druid/loadQueue<br/>
