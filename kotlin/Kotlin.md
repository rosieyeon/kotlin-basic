## Null

- !!로 null이 아님을 개발자가 보장할 수 있다

```kotlin
var number2: Int?=null
var number3: Int? 10
val number4: Int? = number2!! + number3!!
```

- 하지만 실제로 null인 경우에는 NPE(NullPointException이 발생)
- 따라서 정말 100% 확신이 있는 경우가 아니라면 사용하지 말기

<br>



## 객체지향

- 객체를 통해서 문제 또는 원하는 바를 해결
- 객체
  - 축구게임
    - A: 축구선수, 심판, 경기장, 관중 → 객체(object)
    - B: 사람, 공, 호루라기, 경기장
  - A안이 좋은지 B안이 좋은지 구별하기 위해서는 지식이 아니라 경험이 중요
  - 객체를 어떻게 구성하는지가 노하우이자 개발을 잘하는 방법
    - 객체지향을 잘하기 위해서는 경험이 필요하니 서두를 필요가 없음 (하루아침에 해결 안됨)
- 객체지향을 이해하는데 있어서 가장 중요한 문법적인 요소가 class
  - class를 통해서 객체를 만들 수 있기 때문임

<br>

## 클래스

- 객체(object)를 만드는 문법적인 요소
- 설명서 (해당 클래스를 통해서 객체를 만드는 방법)
- 객체의 기능에 대한 설명

<br>



## 생성자

- 객체를 만드는 방법

- Primary constructor(주 생성자)

  - 클래스 이름 옆에 괄호로 둘러쌓인 코드
  - 클래스를 통해서 객체를 만드는데 필요한 재료를 적어준다
    - 재료이름(변수명): 재료타입(변수타입)
  - 반드시 한개만 존재함
  - constructor 키워드를 생략할 수 있음

- Secondary construnctor(부 생성자)

- init 블록 (초기화 블록) 블록 → {}

  - 초기화시에 필요한 작업을 하는 곳

  

- 주생성자 실습 코드

```kotlin
//클래스를 선언하는 방법
class Person {}

//주생성자 -> 풀버전(생략이 없는 버전)
class User1 constructor(name:String) {
  val userName: String // 클래스 속성(property)은 init 블록에서 초기화된다
  
  init { // 클래스가 새성될 때(클래스를 통해서 객체를 만들때) 호출한다
    println(name)
    userName = name
  }
}

// 클래스를 호출하는 방법 -> 클래스를 통해서 객체를 만드는 방법
// 클래스를 호출 -> 인스턴스화 (Instance)
// 객체 -> object, instance
val user = User1(name:"yeon")

// 주생성자 ->. init을 생략하는 방법
class User2 constructor(name: String) {
  val userName: String = name
}
val user = User2(name:"yeon")

//주생성자 -> constructor 생략
class User3 (name:String) {
  val userName: Sring = name
}
val user = User3(name:"yeon")

// 주생성자 -> 기본값
class User4 (name: String = "yeon") {
  val userName : String = name
}
val user = User4()

// 생성자에서 받는 속성이 복수개인 경우
class User5 constructor(age: Int, name: String) {
  val age: Int
  val name: string
  
  init {
    this.age = age // this는 클래스 자체를 의미한다 (User5)
    this.name = name
  }
}

// 주생성자 -> 생략할 수 있는 모든 걸 생략
class Useruser (val userName: String) {
}

// .의 의미 -> ~의
val user5 = User5(age: 20, name:"yeon")
println(user5.age)
// user5.age -> user5의 age
```



- 부생성자 실습 코드

```kotlin
// 부생성자 (Secondary Constructor)
// constructor 키워드 생략 불가능
// 주생성자에는 객체를 만들기 위한 필수 조건이 있다면, 부생성자에게는 옵션 느낌으로 부가적인 조건
// 부생성자에는 주생성자에서 필요한 조건을 포함하고 있어야 한다
// 부생성자는 주생성자에게 생성을 위임해야한다
class User6(name: String) {
  var age: Int = 0
  val name: String
  
  init {
    println("init")
    this.name = name
  }
  
  // 부생성자는 클래스명 우측에 올 수 없다 -> 클래스의 본문에 있어야함
  constructor(name: String, age: Int) : this(name){
    this.age = age
  }
  
  // 부생성자는 복수개 존재할 수 있다
  constructor (nickname: String) {
    
  }
}
// val user6 = User6(name="yeon")
// println(user6.name)
val user6_2 = User6(name:"yeon", age:20)
println(user6_2.age)

// 실행순서: 부생성자 호출 -> 부생성자 안에 있는 주생성자 호출 -> init 블록 호출 -> 부생성자 본문 실행
// 클래스 속성에서 초기화를 시켜주지 않아도 되는 이유
//	- 초기화블록에서 초기화를 보장해주기 때문 -:> 클래스가 생성될 때 초기화블록이 무조건 실행됨
//	- 초기화블록에 없는 속성은 초기화를 선언할 때 초기화해줘야 한다

// 주생성자가 없는 것처럼 보이고 부생성자만 있을 때 부생성자가 주생성자처럼 보인다. 하지만 부생성자 맞음!
// 주생성자는 코틀린이 자동으로 만들어준다
// 주생성자가 없기 때문에 this() 생성자를 이용해 생성을 위임할 필요가 없다
// 굳이 이런식으로 클래스는 만들지는 않는다
class User7 {
  val age: Int
  val name: String
  
  constructor(age: Int, name: String) {
    this.age = age
    this.name = name
  }
}
```



## 클래스 속성 (Property)

```kotlin
class User7 {
  val age: Int
  val name: String
  
  constructor(age: Int, name: String) {
    this.age = age
    this.name = name
  }
}
```

- 속성: age, name
- val user = User7(20. "yeon")
- println(user.age) → 20 출력 → 코틀린이 getter를 호출해준다
- user.age = 30 → 30으로 할당 → 코틀린이 setter를 호출해준다



- getter/setter
  - getter:  클래스의 속성에 접근할 때
  - setter:  클래스의 속성의 값을 설정할 때

- late init (초기화를 미루겠다!)

- ```kotlin
  class User7 {
    lateinit var age: Int
    lateinit var name: String
  }
  ```

  - var로 선언한 프로퍼티에만 적용 가능
  - 주생성자에서는 사용할 수 없다
  - getter/setter 적용이 불가능
  - nullable에는 적용이 불가능
  - 기초타입 프로퍼티에는 적용이 불가능
    - 원시자료형(primitive type)
    - int, Int 분류하면 원시자료형을 명시적으로 구분하지만 코틀린은 따로 구분이 없음
    - 원시자료형은 String을 제외한 우리가 흔히 알고있는 자료형
  - isInitialized로 초기화 여부를 확인해야함