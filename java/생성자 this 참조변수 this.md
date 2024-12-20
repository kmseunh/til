# 생성자 this( ), 참조변수 this

`Java`에서 `this()`와 참조변수 `this`는 모두 클래스 내에서 인스턴스 멤버를 참조하거나 호출하는 데 사용되지만, 그 용도와 사용 방법이 다릅니다.

### 생성자 this( )

생성자 `this()`는 같은 클래스 내의 다른 생성자를 호출하는 데 사용됩니다.

#### 특징

- 반드시 생성자의 첫 문장에서 사용해야 합니다.
- 매개변수 리스트가 일치하는 다른 생성자를 호출합니다.
- 코드 재사용과 간결성을 높이는 데 도움이 됩니다.

#### 예제 코드

```java
class Car {
    String color;
    int door;
    
    Car() {
        this("red", 4); // Car(String, int) 생성자 호출
    }
    
    Car(String color, int door) {
        this.color = color;
        this.door = door;
    }
}
```

### 참조변수 this

참조변수 `this`는 현재 인스턴스를 가리키는 참조변수입니다.

#### 특징

- 인스턴스 메서드 내에서만 사용 가능합니다.
- 인스턴스 변수와 지역 변수를 구분하는 데 주로 사용됩니다.
- 인스턴스의 주소를 저장하고 있습니다.

#### 에제 코드

```java
class Car {
    String color;
    
    Car(String color) {
        this.color = color; // 인스턴스 변수 color에 매개변수 color 값 할당
    }
}
```

#### 사용 시 장점

**1. 코드 가독성 향상:** 인스턴스 변수와 지역 변수를 명확히 구분할 수 있습니다.
**2. 코드 재사용:** 생성자 `this()`를 사용하면 다른 생성자의 코드를 재사용할 수 있어 중복을 줄일 수 있습니다.
**3. 유지보수 용이:** 생성자 간의 유기적 연결로 인해 수정 시 더 적은 코드만 변경하면 되어 유지보수가 쉬워집니다.
**4. 인스턴스 자신을 참조:** 메서드에서 인스턴스 자신을 참조할 때 `this`를 사용하여 명확하게 표현할 수 있습니다.
