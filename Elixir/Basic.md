# Basic of Elixir
---
## Get Started
#### Elixir 설치하기
[해당링크](http://elixir-lang.org/install.html)에서 자신의 **운영체제에 맞는 방법으로** Elixir를 설치한다.  
#### 기본적인 데이터 타입  
###### 정수  
2진수, 8진수, 그리고 16진수도 사용할 수 있다.  
###### 실수  
Elixir에서 실수는 **소수점 앞뒤로 한 개 이상의 숫자가 필요하며** 이를 어길시 syntax error가 발생한다.  
실수는 배정밀도(64bit double precision)로 부동 소수점 숫자를 처리하고, `e`를 사용하여 10의 지수를 표현할 수도 있다.  
###### 부울 값  
Elixir에서는 `true`와 `false`로 부울 값을 표현할 수 있고, `false`와 `nil`만을 거짓으로 취급한고,  나머지는 전부 참으로 간주한다.  
###### 애텀  
애텀은 **이름이 그래도 값이 되는** 상수이다. **Ruby에서 사용되는 심볼과 비슷한 느낌이라고 한다.**  
```Elixir
iex> :foo
:foo
iex> :foo == :bar
flase
```
부울 값 **`true`와 `false`도 애텀이다.** 각각 `:true`와 `:false`로도 표현할 수 있다.  
```Elixir
iex> true |> is_atom
true
iex> :true |> is_boolean
true
iex> :true === true
true
```
Elixir에서 사용하는 모듈의 이름도 애텀이다.  
`Myapp.MyModule`는 올바른 애텀이다. **아직 정의하지 않았더라도** 올바른 애텀이다.  
애텀은 Erlang 라이브러리에서 모듈을 참조할 때에도 사용된다.  
###### 문자열  
Elixir에서 문자열은 내부적으로 UTF-8로 인코딩되며, 큰따옴표 두 개로 감싸 표현한다.  
문자열 내부에서 줄바꿈과 이스케이프도 할 수 있다.  
```Elixir
iex> "foo
...> bar"
"foo\nbar"
```
---
#### 기본적인 연산  
###### 논리 연산  
Elixir에서 논리 연산자로 `||`와 `&&`, `!`는 타입에 관계없이 사용할 수 있다.  
하지만, `and`, `or`, `not`은 **반드시 첫번째 인자가 부울값 이어야 한다.**  
```Elixir
iex> true and 42
42
iex> false or true
true
iex> not false
true
iex> 42 and true
** (ArgumentError) argument error: 42
iex> not 42
** (ArgumentError) argument error
```
###### 비교 연산  
다른 언어에서의 비교 연산자를 Elixir에서도 사용할 수 있다.  
*`==`, `!=`, `===`, `!==`, `<=`, `>=`, `<`, `>`*  
Elixir에서는 비교 연산자를 사용할 때, 타입에 관계없이 비교할 수 있다.  
`<`와 `>`를 사용할 때에는 값이 같을 때, 타입별로 결정되는데, 다음과 같다.  
```
숫자 < 애텀 < 참조 < 함수 < 포트 < pid < 튜플 <
맵 < 리스트 < 비트스트링
```  
이를 이용하여 타입별로 정렬할 수도 있다.  
---
#### 문자열  
###### 문자열 내부 식 전개  
```Elixir
iex> name = "Sean"
iex> "Hello #{name}"
"Hello Sean"
```  
위와 같이 문자열의 내부에서 변수를 사용 할 수 있다.  
###### 문자열 합치기  
```Elixir
iex> name = "Sean"
iex> "Hello " <> name
"Hello Sean"
```  
위와 같이 `<>`연산자로 문자열을 합칠 수 있다.  
