# Java에서 두 변수의 값을 교환하는 방법

Java에서 두 변수의 값을 교환하는 방법은 몇 가지가 있습니다. 가장 기본적인 방식은 임시 변수를 사용하는 방법이고, 다른 방법으로는 산술 연산이나 비트 연산을 사용할 수도 있습니다.

## 1. 임시 변수를 사용하는 방법

이 방법은 메모리를 조금 더 사용하지만, 코드가 명확하고 직관적이기 때문에 가장 널리 사용됩니다.

#### 예제 코드

```java
int a = 10;
int b = 20;

int temp = a;  // a의 값을 임시 변수 temp에 저장
a = b;         // b의 값을 a에 대입
b = temp;      // temp의 값을 b에 대입

System.out.println("a: " + a); // 출력: 20
System.out.println("b: " + b); // 출력: 10
```

- `temp`는 a의 값을 잠시 저장하는 역할을 합니다.
- 그 후, b의 값을 a에 대입하고, `temp`에 저장된 a의 원래 값을 b에 대입하여 두 값을 교환합니다.

## 2. 산술 연산을 사용하는 방법

이 방법은 추가 메모리를 사용하지 않지만, 산술 연산으로 인한 오버플로우 위험이 있을 수 있기 때문에 숫자의 범위가 매우 큰 경우 주의가 필요합니다.

#### 예제 코드

```java
int a = 10;
int b = 20;

a = a + b;  // a는 a와 b의 합을 가짐 (a = 10 + 20 = 30)
b = a - b;  // b는 이제 원래의 a 값을 가짐 (b = 30 - 20 = 10)
a = a - b;  // a는 이제 원래의 b 값을 가짐 (a = 30 - 10 = 20)

System.out.println("a: " + a); // 출력: 20
System.out.println("b: " + b); // 출력: 10
```

- a에 a와 b의 합을 저장합니다.
- b는 이제 a와 b의 합에서 b를 뺀 값, 즉 원래 a의 값을 가지게 됩니다.
- 마지막으로 a는 a와 b의 합에서 새로 저장된 b 값을 빼므로, 원래 b의 값을 가지게 됩니다.

## 3. 비트 연산을 사용하는 방법 (XOR 교환)

비트 연산을 사용하면 임시 변수를 사용하지 않고도 두 변수를 교환할 수 있습니다.

#### 예제 코드

```java
int a = 10;
int b = 20;

a = a ^ b;  // XOR 연산을 통해 a와 b의 값을 비교 후 a에 저장
b = a ^ b;  // b는 이제 원래의 a 값을 가짐
a = a ^ b;  // a는 이제 원래의 b 값을 가짐

System.out.println("a: " + a); // 출력: 20
System.out.println("b: " + b); // 출력: 10
```

- XOR 연산(^)은 두 비트가 다를 때 1을 반환하고, 같으면 0을 반환합니다.
- 이 방법을 통해 a와 b를 임시 변수를 사용하지 않고 교환할 수 있습니다.
- 하지만 비트 연산을 사용하기 때문에 코드가 직관적이지 않으며, 디버깅 시 어려울 수 있습니다.