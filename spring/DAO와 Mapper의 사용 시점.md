# DAO와 Mapper의 사용 시점

Mapper와 DAO(`Data Access Object`)는 데이터베이스와 애플리케이션 간의 상호작용을 처리하는 방식에서 차이가 있으며, 각기 다른 시나리오에서 적합하게 사용됩니다.

## DAO (Data Access Object)

- DAO는 데이터베이스에 접근하여 데이터를 조회하고 조작하는 기능을 담당하는 객체입니다.
- 일반적으로 인터페이스와 구현 클래스로 구성됩니다.
- SQL 쿼리를 직접 작성하고 실행하는 코드가 포함됩니다.
- JDBC나 JPA 등 다양한 데이터 접근 기술을 사용할 수 있습니다.
- 저수준 데이터 접근 로직과 비즈니스 로직을 분리하는 데 사용됩니다.

## Mapper

- MyBatis 3.0부터 도입된 개념으로, XML에 작성된 SQL을 호출하기 위한 인터페이스입니다.
- 단순 인터페이스로만 구성되며, 구현 클래스가 필요 없습니다.
- SQL은 XML 파일에 작성되고, 인터페이스의 메서드와 매핑됩니다.
- MyBatis가 런타임에 구현체를 자동으로 생성합니다.
- 코드가 간결해지고 타입 안정성이 향상됩니다.

### 주요 차이점

#### 구조

- **DAO:** 인터페이스와 구현 클래스로 구성
- **Mapper:** 인터페이스만 존재

#### SQL 작성 위치

- **DAO:** 주로 Java 코드 내에 작성
- **Mapper:** XML 파일에 작성

#### 데이터 접근 기술

- **DAO:** 다양한 기술 사용 가능 (JDBC, JPA 등)
- **Mapper:** MyBatis에 특화됨

#### 코드 복잡성

- **DAO:** 상대적으로 더 많은 코드 작성 필요
- **Mapper:** 간결한 코드로 구현 가능

#### 유지보수

- **DAO:** SQL 변경 시 Java 코드 수정 필요
- **Mapper:** XML만 수정하면 되어 유지보수 용이

#### 타입 안정성

- **DAO:** 문자열 기반 메서드 호출로 오류 가능성 존재
- **Mapper:** 컴파일 시점에 오류 검출 가능

### Mapper 인터페이스 사용이 적합한 경우

- **MyBatis 3.0 이상 사용 시:** Mapper 인터페이스는 MyBatis 3.0부터 도입된 최신 방식으로, 최신 기능을 활용할 수 있습니다1.
- **간결한 코드 선호 시:** Mapper는 인터페이스만으로 구현이 가능하여 코드가 간결해집니다.
- **유지보수 용이성 중시:** SQL 변경 시 XML 파일만 수정하면 되어 유지보수가 용이합니다.
- **타입 안정성 중요 시:** Mapper 인터페이스는 컴파일 시점에 오류를 검출할 수 있어 타입 안정성이 높습니다.
- **IDE의 코드 지원 활용:** Mapper 인터페이스를 사용하면 IDE에서 제공하는 코드 어시스트 기능을 활용할 수 있습니다.

### DAO 패턴 사용이 적합한 경우

- **다양한 데이터 접근 기술 사용 시:** DAO는 JDBC, JPA 등 다양한 데이터 접근 기술을 사용할 수 있어 유연성이 높습니다.
- **복잡한 비즈니스 로직 포함 시:** DAO 클래스에서 복잡한 비즈니스 로직을 구현할 수 있습니다.
- **레거시 시스템 유지보수:** 기존에 DAO 패턴으로 구현된 시스템을 유지보수할 때 일관성을 위해 DAO를 계속 사용할 수 있습니다.
- **추상화 수준 높은 설계 필요 시:** DAO 패턴은 데이터 접근 로직을 추상화하여 높은 수준의 설계가 가능합니다.
결론

프로젝트의 성격에 따라 적합한 방식을 선택해야 하며, 경우에 따라서는 DAO와 Mapper의 혼용이 최적일 수 있습니다.
특히, MyBatis를 사용하는 프로젝트에서 더 가벼운 데이터 접근 및 유지보수가 필요하다면 Mapper 방식이 적합하고, 보다 복잡한 트랜잭션 처리나 데이터베이스 독립성이 필요하다면 DAO가 적합할 것입니다.
