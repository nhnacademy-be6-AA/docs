> <h2>ELK stack</h2>

ELK = Elasticsearch + Logstash + Kibana

1. 데이터 수집/정제 Ingest Pipeline
2. 데이터 저장 ElasticSearch
3. 데이터 시각화 Kibana

![image](https://github.com/user-attachments/assets/5974e917-d8e5-466b-9657-9bd03969d198)

</br>
</br>
</br>

> <h2>RDB와의 차이</h2>

||ES|RDB|
|--|-------------|----|
||**분산형** 검색 엔진<br>대량의 데이터 실시간 처리, 분석 특화|데이터의 정합성과 구조화된 데이터 관리에 초점|
||Inverted index를 사용<br>= 대량의 데이터에서 원하는 정보 빠르게 검색<br>(온라인 쇼핑몰, 뉴스 포털, ...)|데이터의 정합성과 안정성에 더 큰 가치 <br>= 트랜잭션, 롤백, 업데이트<br>(은행, 금융, 의료, ...)|
||Cluster -> Index -> Shard -> document| DB -> table -> Row/Column |
||Index<br>(독립적)|DB|
||Shard|Partition|
||Type<br> (독립적이지 않음)| Table |
|| Document</br>(단어를 기반으로 데이터 저장) | Row |
|| Field |Column|
||Mapping|Schema|
||Query DSL (JSON기반 RESTful API)<br>(GET, PUT, POST, DELETE)|SQL<br>(SELECT, UPDATE, INSERT, DELETE)|
||![image](https://github.com/user-attachments/assets/b593fccb-eead-40f2-a90b-753fe6d75da2)|![image](https://github.com/user-attachments/assets/ee4694f7-23b8-4835-a818-a69222bba43e)|

```json
{
    "query": {
      "bool": {
        "must": [
          { "match": { "user": "kimchy" } },
          { "range": { "age": { "gt": 30 } } }
        ]
      }
    }
  }
  ``` 
```sql
  SELECT * FROM users WHERE age > 30;
  ``` 


<br>
<br>
<br>
<br>

> <h4>전체 구성도</h4>

![image](https://github.com/user-attachments/assets/a6636db8-6ed6-407d-bcc0-b144c6729816)

<br>
<br>
<br>
<br>

> <h4>특징</h4>


* 로그분석, 실시간데이터분석, 풀 텍스트검색에 사용</br>
= 대규모 데이터를 실시간으로 분석하고 모니터링하는데 성능▲

* **dense_vector 문서 유형을 통한 벡터 검색 지원**</br>
= 텍스트 시멘틱 검색 + 이미지 유사성 검색, 특정필드 가중치 검색</br>
= 자연어처리가능 = 동의어, 유의어, 형태소분석 플러그인 지원

* Schemaless<br>
= 비정형
* Multi-tenancy<br>
= 검색할 필드명이 같으면 서로 다른 여러개의 인덱스를 한번에 조회

* ex)<br>
웹사이트에서 사용자의 행동 로그를 분석하여 사용자 경험 개선</br>
보안 로그를 분석해 비정상적인 접근을 식별

![image](https://github.com/user-attachments/assets/ceedf850-5e43-4a49-aa0b-e1f02d119d6e)

<br>
<br>

> <h4>용어</h4>

* 클러스터(Cluster)
  + 노드의 집합
  + 모든 노드를 포괄하는 통합 색인화 및 검색기능 제공

* 노드(Node)
  + Elasticsearch를 구성하기 위한 하나의 인스턴스, 프로세스 단위
    + Master Node : 클러스터 관리, 인덱스 생성, 삭제
    + Data Node : Document가 저장되는 노드, 컴퓨터 리소스를 많이 소모함
    + Ingest Node : Document의 전처리, 데이터포맷변경, 전처리 파이프라인
    + Coordinate Node : 검색이나 집계시 요청 전달, 분산(RR방식)

* 인덱스(Index)
  + document의 집합
  + 논리적인 저장단위

* 샤드(Shard)
  +  물리적으로 노드에 저장되는 단위
     + 프라이머리 샤드
       + 데이터가 나뉘어 지는 단위, 설정된 개수에 따라 각 노드에 분산 저장
       + 인덱스 생성후에는 프라이머리 샤드 개수 변경 불가능
     + 레플리카 샤드
       + 샤드의 복제본
       + 생성된 프라이머리 샤드를 세트단위로 지정하여 복제
       + 아래의 '인덱스와 샤드' 링크 참고
* 타입(Type)
  + 같은 Index + 다른 Type + 같은 Field명이면 동일한 Lucene Engine 필드로 처리
  + (completely removed after v8.0) 



<br>
<br>
<br>
<br>



<br>


>참고 및 출처링크:</br>

인덱스와 샤드 :<br>
[https://leediz.tistory.com/20?category=950404]

클러스터 :<br>
[https://trace90.tistory.com/entry/ElasticSearch-%ED%81%B4%EB%9F%AC%EC%8A%A4%ED%84%B0-%EA%B0%9C%EB%85%90]

모델링 방법론 :<br>
[https://s-core.co.kr/insight/view/%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%EC%84%9C%EC%B9%98elasticsearch%EC%97%90%EC%84%9C-%EA%B4%80%EA%B3%84%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-%ED%95%98%EA%B8%B0/]

문법 :<br>
[https://github.com/kimjmin/elastic-demo/blob/master/demos/get-started/elasticsearch-7x.md]
<br>
<br>
<br>
<br>
<br>
<br>
https://velog.io/@munang/ElasticSearch-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90<br>
(기본개념, elasticsearch.yml)<br>
https://f-lab.kr/insight/elasticsearch-vs-rdb<br>
(엘라스틱서치와 RDB의 차이점과 선택 기준)<br>
https://ghkdqhrbals.github.io/portfolios/docs/elasticSearch/2022-12-31-elastic-search/<br>
(Elastic Search의 개념 및 RDB와의 차이점)<br>
https://velog.io/@dat0802/Elasticsearch%EC%99%80-RDB%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC<br>
(Elasticsearch와 RDB에 대하여)<br>
