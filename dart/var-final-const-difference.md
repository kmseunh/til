# var, final, const의 차이

`Dart`는 변수를 선언할 때 `var`, `final`, `const` 세 가지 변수를 제공합니다.

&nbsp;

## var

`var` 변수는 변수를 선언할 때 사용됩니다. `Dart`는 정적 타입 지정 언어이지만, `var`를 사용하면 변수의 타입을 명시적으로 선언하지 않아도 됩니다. 대신 컴파일러가 할당된 값의 타입을 추론합니다.

```dart
var name = 'John';
```

- 변수 `name`은 문자열(`string`) 타입으로 추론됩니다.
- 변수를 선언할 때 초기값을 할당하지 않으면 기본적으로 `null`로 초기화됩니다.

&nbsp;

## final

`final` 변수는 한 번 할당된 이후에는 값을 변경할 수 없는 변수를 선언할 때 사용됩니다. `final` 변수는 상수와 유사하지만 런타임 상수가 아닌 컴파일타임 상수입니다.

```dart
final name = 'John';
```

- `final` 변수는 선언할 때 초기화되어야 하고, 초기화 이후에는 새로운 값을 할당할 수 없습니다.

&nbsp;

## const

`const` 변수는 컴파일타임 상수를 선언할 때 사용됩니다. `const` 변수는 컴파일 시간에 알려진 값으로 초기화되어야 합니다.

```dart
const name = 'John';
```

- `const` 변수는 컴파일 시간에 상수식(`compile-time constant`)으로 평가됩니다.

> 프로그램이 실행될 때 변경되지 않습니다.
