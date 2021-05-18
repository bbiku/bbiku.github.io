---
category: Studies
tags: [Elasticsearch]
---

# 8. Aggregation

- SQL의 Group by 같은 기능을 한다.
- 숫자연산을 할 수 있는 값들에 대한 집계 수행 (Metrics)
- 범위나 keyword 값 등으로 document들을 그룹화 (Bucket)

## Metrics

### Stats

- count, min, max, avg, sum 제공

```json
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "stats_price": {
      "stats": {
        "field": "건물면적"
      }
    }
  }
}
```

## Percentiles

```json
# 지정구간의 값 보기
GET realprice/_search
{
  "size": 0, 
  "aggs": {
    "NAME": {
      "percentiles": {
        "field": "건물면적",
        "percents": [0, 25, 50, 75, 100]
      }
    }
  }
}

# field값으로 백분위 위치 검색
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME": {
      "percentile_ranks": {
        "field": "건물면적",
        "values": [40, 65, 85, 2804]
      }
    }
  }
}
```

## Cardinality

- Field 분포값을 검색
- 중복 제외

```json
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME": {
      "cardinality": {
        "field": "자치구명"
      }
    }
  }
}
```

## Range

- from(이상),  to (미만)

```json
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME": {
      "range": {
        "field": "건물면적",
        "ranges": [
          {"to":60},
          {"from": 60, "to": 85},
          {"from": 85}
        ]
      }
    }
  }
}
```

## Histogram

```json
# 기본
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME": {
      "histogram": {
        "field": "건축년도",
        "interval": 10,
        "min_doc_count": 1
      }
    }
  }
}

# 날짜
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME":{
      "date_histogram": {
        "field": "@timestamp",
        "interval": "year", 
        "format": "yyyy-MM-dd"
      }
    }
  }
}

# 문자열별 집계
GET realprice/_search
{
  "size": 0,
  "aggs": {
    "NAME": {
      "terms": {
        "field": "자치구명"
      }
    }
  }
}
```

## Pipeline aggregation

```json

```

## 활용