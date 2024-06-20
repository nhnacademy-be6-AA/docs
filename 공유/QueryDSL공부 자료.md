설정 및 사용법 : https://velog.io/@weonest/QueryDSL-%EC%82%AC%EC%9A%A9
              : https://adjh54.tistory.com/485#4.%20JPAQueryFactory%20%EA%B5%AC%EC%84%B1-1
api docs : https://javadoc.io/doc/com.querydsl/querydsl-jpa/latest/index.html
-----

```
dependency(maven) : 
        <dependency>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-jpa</artifactId>
            <version>5.1.0</version>
            <classifier>jakarta</classifier>//javax -> jakarta 변경 필수
        </dependency>

        <dependency>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-apt</artifactId>
            <version>5.1.0</version>
            <classifier>jakarta</classifier>
        </dependency>
```
