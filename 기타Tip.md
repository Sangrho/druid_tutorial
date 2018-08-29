## 로그 설정하는 방법

configuration에서,로그를 보고 싶어서 log4j를 추가할때 broker, coordinator  등 다섯개 컴퍼넌트에 추가를 하고_ common에도 추가를 하면 로그가 쌓이지 않는다.<br/>
왜냐하면_common에 있는걸 먼저 읽기 때문에 _common에는 log4j를 추가하지 않는다.<br/><br/>

## Druid Historical Multi Path

    druid.service=druid/historical
    .
    .
    # Segment storage
    druid.segmentCache.locations=[{"path":"/data1/druid/segment-cache","maxSize":220000000000},{"path":"/data2/druid/segment-cache","maxSize":220000000000},{"path":"/data3/druid/segment-cache","maxSize":220000000000},{"path":"/data4/druid/segment-cache","maxSize":220000000000},{"path":"/data5/druid/segment-cache","maxSize":220000000000}]
    .
    .
    
(* 주의 : druid.segmentCache.locations 에 있는 디렉토리들은 직접 만들어놔야 한다.)

## MiddleManager work.capacity 계산 방법

![image](https://user-images.githubusercontent.com/4033129/44766980-e3cb5d80-ab96-11e8-8aa2-362f09093c3c.png)

[ 시나리오 ]<br/>
![image](https://user-images.githubusercontent.com/4033129/44767245-0742d800-ab98-11e8-8244-78636e5eeb92.png)

## Deep Storage(HDFS) 에 있는 Segment 삭제
Overlord 에 쿼리를 보내는 방식을 사용한다.<br/>
(http://${Overlord Address}:{Overlord Port}/druid/indexer/v1/task)<br/>
        {<br/>
            "type": "kill",<br/>
            "id": "${아무거나 쓰면 되고,관리하기 쉽게 날짜를 쓴다}",<br/>
            "dataSource": "${DataSource}",<br/>
            "interval" : "${StartTimeStamp}/${EndTimeStamp}"<br/>
        }<br/>
        <br/><br/>
 ## Retention 기간이 지난 데이터를 HDFS 에 다시 올리는 방법
 
 ![image](https://user-images.githubusercontent.com/4033129/44767435-d911c800-ab98-11e8-8147-632ade7acc9b.png)
<br/><br/>
## Overlord 가 job 을 균등하게 사용하기 위한 방법
Overlord 에 아래와 같은 쿼리를 보내는 방식을 사용한다.<br/>
(http://${Overlord Address}:{Overlord Port}/druid/indexer/v1/worker)<br/>
        {<br/>
          "selectStrategy": {<br/>
            "type": "equalDistribution"<br/>
          }<br/>
        }<br/>
<br/><br/>

## Replication 속도 높이는 방법

1. Coordinator Web 에서 왼쪽 상단의 'edit cluster cluster configuration' 클릭<br/>
![image](https://user-images.githubusercontent.com/4033129/44767546-432a6d00-ab99-11e8-9a8a-b2d23a6db4a9.png)<br/>
2. maxSegmentsToMove, replicationThrottleLimit 수정<br/>
![image](https://user-images.githubusercontent.com/4033129/44767549-445b9a00-ab99-11e8-9933-49ef9448be11.png)<br/><br/>

## Druid 설정 변경 이력 확인
1.Commenct 를 아래와 같이 남긴다.<br/>
![image](https://user-images.githubusercontent.com/4033129/44767582-6bb26700-ab99-11e8-80c9-64e9ec4592c0.png)<br/>


2.DB 에서 아래와 같이 확인할 수 있다.<br/>
![image](https://user-images.githubusercontent.com/4033129/44767586-6ce39400-ab99-11e8-9735-0d86a6136623.png)<br/><br/>
