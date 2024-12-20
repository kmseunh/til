# LEFT JOIN과 INNER JOIN의 차이점

`LEFT JOIN`과 `INNER JOIN`은 SQL에서 두 테이블을 결합하는 데 사용하는 주요 조인 방식입니다. 이 두 가지 조인 방식은 데이터를 결합하는 방식에서 차이가 있습니다.

#### INNER JOIN

`INNER JOIN`은 두 테이블 간의 공통된 값을 가진 레코드만 반환합니다.
즉, 두 테이블에서 일치하는 데이터만 결과에 포함됩니다.

#### LEFT JOIN (또는 LEFT OUTER JOIN)

`LEFT JOIN`은 왼쪽 테이블의 모든 레코드를 반환하고, 오른쪽 테이블의 일치하는 레코드가 있으면 그 레코드도 포함합니다.
오른쪽 테이블에서 일치하는 레코드가 없는 경우, 해당 컬럼은 `NULL`로 반환됩니다.

## 차이점

### 결과 집합의 범위

#### INNER JOIN

- 두 테이블의 교집합만 반환합니다.
- 조인 조건을 만족하는 행만 결과에 포함됩니다.

#### LEFT JOIN

- 왼쪽 테이블의 모든 행을 포함하고, 오른쪽 테이블과 일치하는 행을 결합합니다.
- 왼쪽 테이블에 있지만 오른쪽 테이블에 일치하는 행이 없는 경우, 오른쪽 테이블의 컬럼은 `NULL` 값으로 채워집니다.

### 결과 행의 수

#### INNER JOIN

일반적으로 `LEFT JOIN`보다 적은 수의 행을 반환합니다.

#### LEFT JOIN

왼쪽 테이블의 모든 행을 포함하므로 `INNER JOIN`보다 많은 행을 반환할 수 있습니다.

### 사용 사례

#### INNER JOIN

- 두 테이블 간의 관계가 명확하고 일치하는 데이터만 필요할 때 사용합니다.
- 성능 면에서 `LEFT JOIN`보다 유리할 수 있습니다.

#### LEFT JOIN

- 왼쪽 테이블의 모든 데이터를 유지하면서 오른쪽 테이블과의 관계를 보고 싶을 때 사용합니다.
- 데이터의 누락 없이 모든 정보를 확인해야 할 때 유용합니다.

### 성능 고려사항

- 일반적으로 `INNER JOIN`이 `LEFT JOIN`보다 성능이 좋습니다.
- 동일한 결과를 얻을 수 있다면 `INNER JOIN`을 사용하는 것이 바람직합니다.

`JOIN` 연산은 데이터베이스에서 여러 테이블의 관련 데이터를 결합하는 데 중요한 역할을 합니다.
데이터 정규화, 효율적인 저장 및 관리, 그리고 데이터 일치성과 무결성 유지를 위해 `JOIN`이 사용됩니다.
