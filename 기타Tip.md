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

[ 시나리오 ]
![image](https://user-images.githubusercontent.com/4033129/44767245-0742d800-ab98-11e8-8244-78636e5eeb92.png)
