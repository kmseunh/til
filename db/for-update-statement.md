# FOR UPDATE 구문

`FOR UPDATE`는 SQL에서 사용되는 구문으로, 트랜잭션 내에서 특정 레코드를 선택하고 해당 레코드에 대한 잠금을 설정하기 위해 사용됩니다. 이를 통해 다른 트랜잭션이 동일한 레코드를 수정하거나 삭제하지 못하도록 방지할 수 있습니다.

## FOR UPDATE의 역할

#### 레코드 잠금

- `FOR UPDATE`는 트랜잭션이 실행되는 동안 선택된 레코드를 잠금(`Lock`)으로 보호합니다.
- 이러한 잠금은 다른 트랜잭션이 이 레코드를 수정하거나 삭제하려고 할 때 대기 상태에 들어가게 하며, 잠금이 해제될 때까지 기다려야 합니다.
- 이 방식은 데이터 일관성을 유지하고 동시성 문제를 방지하는 데 매우 유용합니다.

#### 트랜잭션 처리

- 트랜잭션에서 `FOR UPDATE`를 사용하면 해당 레코드에 대해 안전하게 업데이트 작업을 수행할 수 있습니다.
- 특히 은행 거래와 같은 중요한 트랜잭션 처리에서는, 계좌 잔액을 확인한 후 잔액을 수정하는 과정에서 데이터의 일관성을 유지하는 것이 매우 중요합니다.

```sql
-- 예제 쿼리문
BEGIN;

SELECT balance FROM accounts WHERE account_id = 12345 FOR UPDATE;

-- 위에서 선택한 계좌에 대해 잔액을 업데이트하는 작업 수행
UPDATE accounts SET balance = balance - 100 WHERE account_id = 12345;

COMMIT;
```

- `SELECT ... FOR UPDATE`는 특정 계좌의 잔액을 조회하며 동시에 해당 레코드를 잠금으로 설정합니다. 이렇게 하면 다른 트랜잭션이 동일한 계좌의 잔액을 수정하지 못하도록 합니다.

## FOR UPDATE 사용 시와 미사용 시의 차이

### 데이터 일관성

- **사용 시:** 특정 트랜잭션이 완료되기 전까지 다른 트랜잭션이 동일한 레코드에 접근하여 수정할 수 없으므로 데이터의 일관성을 유지할 수 있습니다.
- **미사용 시:** 동시에 여러 트랜잭션이 같은 레코드를 수정하려고 할 경우, 데이터의 일관성이 깨질 수 있으며, 이는 “갱신 손실(Lost Update)” 같은 문제로 이어질 수 있습니다.

### 경합 상황 (Race Condition)

- **사용 시:** 한 트랜잭션이 레코드를 잠그면 다른 트랜잭션은 잠금이 해제될 때까지 대기하게 됩니다. 이를 통해 경합 상황을 방지할 수 있습니다.
- **미사용 시:** 두 트랜잭션이 동시에 동일한 데이터를 수정하려고 하면 예기치 않은 결과가 발생할 수 있으며, 이는 데이터 무결성에 문제를 일으킬 수 있습니다.

### 성능

- **사용 시:** 잠금으로 인해 대기 시간이 증가할 수 있습니다. 따라서 높은 동시성이 요구되는 환경에서는 성능에 영향을 줄 수 있습니다.
- **미사용 시:** 잠금 없이 작업이 수행되므로 대기 시간이 줄어들어 성능이 향상될 수 있지만, 이는 데이터 무결성의 위험을 감수해야 한다는 의미입니다.
