---
category: Studies
tags: [Elasticsearch]
---

# 3. ES vs RDBMS

# 검색시스템의 구성요소

1. 수집기
    - 정보수집
    - Web에서 필요한 정보를 수집하는 프로그램
    - 크롤러, 스파이더, 웜, 웹로봇 등
2. 스토리지
    - 수집한 데이터를 저장
    - DB에서 데이터를 저장하는 물리적인 저장소
    - 색인한 데이터를 스토리지에 보관
3. 색인기
    - 수집한 데이터를 검색에 적절한 형태로 변환
    - 다양한 형태소 분석기를 조합해 정보에서 의미있는 용어를 추출하고 역색인 구조로 데이터 저장
4. 검색기
    - 색인된 데이터에서 일치하는 문서를 찾는 검색기
    - 검색한 질의를 형태소 분석을 통해 색인기로 저장한 데이터와 비교해 결과를 반환
    - 형태소 분석기에 따라 검색품질이 달라진다.

# RDBMS와 차이점

1. RDBMS
    - DB는 데이터를 통합관리하는 데이터의 집합
    - 저장되는 구조
        - 중복을 제거
        - 정형데이터 구조화
        - 행, 열로 구성
        - 테이블 구조로 저장
    - SQL문을 이용해 원하는 정보 검색가능
    - 텍스트 매칭을 통한 단순한 검색만 가능
    - 텍스트를 여러 단어로 변형하거나 여러 개의 동의어나 유의어를 활용한 검색은 불가
2. 검색엔진
    - DB에서는 불가능한 비정형 데이터를 색인하고 검색할 수 있음
    - 형태소분석을 통해 자연어처리 가능
    - 역색인 구조를 바탕으로 빠른 검색속도 보장

# 용어비교

```html
<table>
<tr>
<th>관계형 데이터베이스</th>
<th>elastic search</th>
</tr>
<tr>
<td>Database</td>
<td>Index</td>
</tr>
<tr>
<td>Table</td>
<td>Type</td>
</tr>
<tr>
<td>Row</td>
<td>Document</td>
</tr>
<tr>
<td>Column</td>
<td>Field</td>
</tr>
<tr>
<td>Schema</td>
<td>Mapping</td>
</tr>
<tr>
<td>Index</td>
<td>Everything is indexed</td>
</tr>
<tr>
<td>SQL/td>
<td>Query DSL/td>
</tr>
</table>
```