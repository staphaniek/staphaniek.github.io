---
layout: post
title: "Mysql Point type 확인하기"
comments: true
---

Mysql은 POINT라는 geometric 타입을 지원합니다.
주로 POINT 타입은 위치 정보의 위경도를 저장하는 경우가 많은데, Mysql Workbench 등 쿼리를 날리는 SW에서 해당 타입을 SELECT 문으로 조회하려면 BLOB 형식으로 나타나 자세한 record의 내용을 확인할 수 없습니다.<br>
테이블 이름을 T, Point type으로 정의된 column을 P라고 할 때,
```Mysql
SELECT
  X(P) AS 'Latitude',
  Y(P) AS 'Longitude'
FROM
  T
```
와 같은 쿼리를 통해 위도, 경도를 추출해낼 수 있습니다.
