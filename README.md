# 4장. 변수

## 4.1 변수란 무엇인가? 왜 필요한가?
먼저 컴퓨터(java script엔진)는 3+5를 계산하기 위해서는 3, 5, +라는 기호들의 의미를 알고 있어야 한다.

컴퓨터에 적용시키면 3, 5는 메모리에 의해 기억되고 +는 cpu에 의해 연산되는 과정을 거친다.

**메모리**는 메모리 셀이라는 1바이트 크기의 집합체이며 각각의 셀마다 고유한 주소를 가진다.

이 주소를 **메모리 주소**라고 부르며 메모리 셀의 위치를 나타낸다.

다시 말해, 3과 5는 고유한 메모리 주소값을 가지는 메모리 셀에 저장되고 CPU가 +기호와 값들을 불러들여 연산이 진행된다.

이 값인 8은 또 다른 메모리 셀에 저장되고 고유한 메모리 주소값을 가진다. 

그러나 실행될때마다 바뀌는 메모리 주소만을 가지고서는 이 값에 접근할 수 없다. 

그래서 우리는 **변수**라는 이름을 사용해 메모리 주소에 접근한다.

쉽게 말해 변수가 포함된 코드가 실행되면 변수는 메모리 공간의 주소와 연결되어 실행된다.

변수에 값을 저장하는 것을 **할당**, 저장된 값을 불러 들이는 것을 **참조**라고 한다.

## 4.2 식별자
변수 이름을 식별자라고 부르며 사람 이름, 물건 이름도 식별자라 할 수 있다.

4.1에서 말했듯이, 식별자는 값을 식별할 수 있어야 한다. 

그러나 식별자는 메모리 셀의 값이 아닌 메모리 주소를 기억 및 저장하고 있다.

우리는 **선언**을 통해 식별자를 만들어낸다.

## 4.3 변수 선언
변수 선언은 변수 생성과 같다. 

자바 스크립트에서는 var, let, const와 같은 키워드를 사용한다. 

`var(변수 선언 키워드) result (변수 이름)` 이렇게 선언문을 작성한다.

변수를 선언하고 값을 할당하지 않았으므로 변수가 가리키는 메모리 주소에는 Undefined라는 값이 자동으로 할당되어 초기화된다.

이때 초기화는 변수가 선언되고 처음으로 값이 할당되는 것을 의미한다.

초기화 과정을 거치지 않으면 메모리 공간에 이전에 사용한 값인 **쓰레기 값**이 남아있는 문제가 생긴다.

따라서 변수를 사용하려면 반드시 먼저 선언과 초기화 과정을 거쳐야 한다. 만약 선언하지 않은 변수의 값을 참조하려 한다면 ReferenceError가 발생한다.

## 4.4 변수 선언의 실행 시점과 변수 호이스팅
```javascript
console.log(score);
var score;
```
위의 코드는 변수를 선언하기 전 변수를 참조한 코드이다.

변수가 선언되고 나서 변수를 활용하여야 올바른 코드이다.

즉, 이 코드는 ReferenceError가 나는게 정상이지만 자바스크립트는 특별하게 코드를 한 줄씩 실행하기 전 평가 과정을 거친다.

평가 과정에서 뒤에 적혀있는 선언문을 먼저 찾아낸 후 실행하기 때문에 오류가 나지 않고 undefined 값으로 남아있는 것이다. 

뒤에 있던 변수 선언문이 앞에 적혀있는 것처럼 작용하는 것을 **변수 호이스팅** 이라고 한다. 

## 4.5 값의 할당
```javascript
var score;
score = 80;
```
위의 코드는 변수 **score** 를 선언한 후 80이라는 값을 **할당**한 코드이다.

```javascript
var score= 80;
```
로도 단축할 수 있다.

위에 말했듯이 var키워드는 선언만하여도 자동으로 undefined 값으로 초기화된다.

그러나 **=**기호를 사용해 undefined에서 80이라는 값으로 변경된 것이다.

메모리 측면에서 보면, 원래의 score 변수가 가리키는 메모리 주소에는 undefined 값이 있다.

80을 할당하므로서 undefined 값이 80으로 바뀌는 것이 아니라 새로운 메모리 공간을 확보해 그 공간으로 변수가 연결되어 80을 저장한다.

## 4.6 값의 재할당
**재할당**은 말그대로 할당한 값에 다시 새로운 값을 할당하는 것이다.
```javascript
var score = 80;
score = 90;
```
위 코드처럼 80으로 할당한 후 90으로 재할당하였다. 값이 바뀌는 재할당은 변수만의 특징이며 재할당을 할 수 없다면 **상수**라고 한다.

할당할때의 메모리 메커니즘과 비슷하게 원래 score 변수는 undefined 값을 가지고 있었으나 80이라는 값으로 할당된다.

이때, score 변수는 80이라는 메모리 공간을 가리키고 다시 90으로 재할당되면 변수는 90이라는 값을 가진 메모리 공간으로 변경된다.

그러면 그 전의 undefined와 80이라는 값을 가진 메모리 공간은 더 이상 쓰지 않겠다는 의미로 여겨져 자동 해제된다.

## 4.7 식별자 네이밍 규칙
식별자는 값을 구별해내는 고유한 이름으로 아래의 정해진 규칙에 따라서 작성해야한다. 

- 식별자는 특수문자를 제외한 문자, 숫자, 언더바, 달러기호로 작성할 수 있다.
- 단, 특수문자, 숫자로는 시작할 수 없다.
- if, import, export와 같은 예약어는 함수 이름으로 사용할 수 없다.
  
이외에도 변수들에 ,(콤마)기호를 사용해 동시에 여러 변수들을 선언할 수 있으나 가독성이 떨어진다.

변수이름을 한글, 일본어와 같이 유니코드 문자로 작성할 수 있으나 되도록 알파벳을 사용한다.

변수는 대소문자를 구별하므로 First라는 변수와 first라는 변수는 각각 다르다.

변수의 이름은 그 의미를 알 수 있도록 명확해야한다.

