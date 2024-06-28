# 시퀀스를 사용하는 이유

시퀀스는 유일한 숫자 값을 생성하는 객체로, 주로 기본 키(`primary key`)와 같은 유일한 식별자(`unique identifier`)를 생성하는 데 사용됩니다.

## 시퀀스를 사용하는 이유

#### 유일한 식별자 생성

데이터베이스에서 각 레코드는 유일하게 식별될 수 있어야 합니다. 시퀀스를 사용하면 중복되지 않는 유일한 숫자 값을 생성하여 각 레코드를 구분할 수 있습니다.

- ex. 고객 테이블에서 각 고객을 유일하게 식별하기 위해 고객 ID를 시퀀스로 생성할 수 있습니다.

#### 병렬 처리 환경에서의 안전성

여러 사용자가 동시에 데이터베이스에 접근할 때, 시퀀스를 사용하면 충돌 없이 유일한 값을 생성할 수 있습니다. 데이터베이스는 시퀀스 값을 안전하게 증가시키므로, 병렬 처리 환경에서도 유일성을 보장할 수 있습니다.

#### 성능 향상

시퀀스를 사용하면 트랜잭션 간의 잠금 경합(`lock contention`)을 줄일 수 있어 데이터베이스 성능이 향상됩니다. 시퀀스는 독립적으로 증가하므로 다른 트랜잭션과의 충돌이 줄어들어 성능이 좋아집니다.

#### 코드의 간결성

시퀀스를 사용하면 유일한 값을 생성하는 로직을 간결하게 작성할 수 있습니다. 이를 통해 코드의 가독성과 유지 보수성이 향상됩니다.