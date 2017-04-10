# Elixir Collection  
---  
## List  
리스트는 값들을 묶어둔 컬렉션이며, **여러타입을** 포함할 수 있고 **중복된 값도** 포함할 수 있다.  
---  
### 관련함수  
---  
#### 리스트 추가  
```Elixir  
iex> list = [3.14, :pie, "Apple"]  
[3.14, :pie, "Appele"]  
iex> ["text"] ++ list  
["text", 3.14, :pie, "Apple"]  
iex> list ++ [0.0174]  
["text", 3.14, :pie, "Apple", 0.0174]  
```  
#### 리스트 이어붙이기  
```Elixir  
iex> [1, 2] ++ [3, 4, 1]  
[1, 2, 3, 4, 1]  
```  
이때, **++/2** 를 사용하는데, 이러한 이름 형식은 **함수와 연산자 이름과** 그 **인자의 개수로** 두 구성요소를 가진다.  
**이름과 인자의 개수는 슬레시(/)로 결합되어** ++/2와 같은 형식이 만들어 진다.  
#### 리스트 빼기  
`--/2`연산자를 이용하여 빼기를 할 수 있다.  
이때, 리스트에 **존재하지 않는 값을 빼도 무방하다.**  
```Elixir  
iex> ["foo", :bar, 42] -- [42, "bar"]  
["foo", :bar]  
```  
중복 값을 뺄때, **오른쪽에 있는 모든 요소에 왼쪽을 비교하여 처음 만난 요소만** 지운다.  
```Elixir  
iex> [1,2,2,4,3,2,4] -- [1,2,3,2]  
[4,2,4]  
```  
리스트 빼기를 할때, 값비교는 **엄격한 비교(`===`)를** 사용한다.  
#### Head/Tail  
`hd`와 `tl`로 리스트의 첫 번째 원소와 그 나머지 원소를 구할 수 있다.  
```Elixir  
iex> hd [3.14, :pie, "Apple"]
3.14
iex> tl [3.14, :pie, "Apple"]
[:pie, "Apple"]
```  
---  
## 튜플  
튜플(tuples)은 리스트와 비슷하지만 **메모리에 연속적으로** 저장된다.  
이 때문에 튜플의 길이를 구하는 것은 빠르지만 수정하는 것은 비용이 비싸다.(?)  
튜플을 정의할 때에는 중괄호를 사용한다.  
```Elixir
iex> {3.14, :pie, "Apple"}
{3.14, :pie, "Apple"}
```  
튜플은 함수가 추가정보를 반환하는 수단으로 자주 사용된다.  
이의 유용함은 패턴 매칭(pattern matching)을 배울 때 더 명확해 진다고 한다.  
---
## 키워드 리스트  
키워드(keyword)와 맵(map) 은 Elixir의 연관 컬렉션 이다.  
Elixir에서 키워드 리스트란 **첫번째 원소가 애텀인** 특별한 튜플을의 리스트이다.  
따라서 키워드 리스트는 리스트와 성능이 비슷하다.
```Elixir
iex> [foo: "bar", hello: "world"]
[foo: "bar", hello: "world"]
iex> [{:foo, "bar"}, {:hello, "world"}]
[foo: "bar", hello: "world"]
```  
키워드 리스트에는 매우 중요한 특징 세 가지가 있다.  
- 모든 키는 애텀이다.  
- 키는 정렬되어 있다.  
- 키는 중복될 수 있다.  
이러한 이유로 키워드 리스트는 **함수에 옵션을 전달하는 데** 가장 많이 사용된다.  
---
## 맵  
맵은 키워드 리스트와 다르게 **키가 어떤 타입이든 될 수 있고,** 순서를 따르지 않다.  
맵은 `%{}`을 이용하여 정의한다.  
```Elixir
iex> map = %{:foo => "bar", "hello" => :world}  
%{:foo => "bar", "hello" => :world}
iex> map[:foo]
"bar"
iex> map["hello"]
:world
```
Elixir 1.2부터는 **변수를 맵의 키로** 이용할 수 있다.  
맵을 정의할 때, 만약 키가 중복된다면 **이전의 값을 새로운 값으로** 교체한다.  
```Elixir
iex> %{foo: "bar", hello: "world"}
%{foo: "bar", hello: "world"}

iex> %{foo: "bar", hello: "world"} == %{:foo => "bar", :hello => "world"}
true
```  
맵에는 위에서 보이듯 **모든 키가 atom인** 맵을 정의하기 위한 문법도 존재한다.  
또다른 문법도 있는데, 이를 사용하여 애텀키를 통해 맵 내부를 열람하거나 수정할 수 있다.  
```Elixir
iex> map = %{foo: "bar", hello: "world"}
%{foo: "bar", hello: "world"}
iex> %{map | foo: "baz"}
%{foo: "baz", hello: "world"}
iex> map.hello
"world"
```
