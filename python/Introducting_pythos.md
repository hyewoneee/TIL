# 도서리뷰 -템 Introducting Python 처음 시작하는 파이썬

# 목차

- [x] 1장. 파이(Py) 맛보기
- [x] 2장. 파이 재료: 숫자, 문자열, 변수
- [x] 3장. 파이 채우기: 리스트, 튜플, 딕셔너리, 셋
- [x] 4장. 파이 크러스트: 코드 구조
- [x] 5장. 파이 포장하기: 모듈, 패키지, 프로그램
- [x] 6장. 객체와클래스
- [x] 7장. 데이터 주무르기
- [x] 8장. 흘러가는 데이터
- [x] 9장. 웹
- [x] 10장. 시스템
- [ ] 11장. 병행성과 네트워크 
- [ ] 12장. 파이 환경 설정 및 도구: 파이써니스타 되기

# 1장 파이(Py) 맛보기

파이썬은 범용의 고수준 언어며 코드를 읽기 쉽다.

- 코드를 **작성하기도 쉽다.**

- 금방 실무에 적용할 수 있는 아주 좋은 학습 곡선을 가지고 있다.

### 파이썬을 쓰면 안 될 때

프로그램이 계산 작업을 많이 하는 경우

- CPU 바운드라 한다.

- 수행하는 계산 작업은 CPU 속도에 의해 결정된다.

파이썬 3에서 작성한 코드는 파이썬 2에서 동작하지 않는다.(파이썬2 →파이썬3도 동작하지 않는다)

- 고치기 어려운 것은 서로 호환되지 않는다.

### 파이썬 철학

	아름다운 것이 추한 것보다 낫다.

	명확한 것이 함축적인 것보다 낫다.

	단순한 것이 복잡한 것보다 낫다.

	복잡한 것이 난해한 것보다 낫다.

	단조로운 것이 뒤엉킨 것보다 낫다.

	분포되어 있는 것이 빽빽한 것보다 낫다.

	가독성은 중요하다.

	특별하 경우라 하더라도 규칙응ㄹ 어길 수 있을 만큼 특별하지 않다.

	비록 실용성이 순수함을 앞선다 할지라도 오류를 절대로 넘기면 안된다.

	분명하게 조용하지 않는 한 모호한 상황에서도 추측하려는 유혹을 떨쳐내야 한다.

	그것을 할 수 있는 분명한 한 가지 방법이 있어야 한다. 그방법이 유일하면 더 좋다.

	네덜란드 사람(파이썬의 창시자를 가리킴)이 아니라면, 처음에 그 방법이 분명하지 않을 수도 있다.

	지금 하는 것이 하지 않는 것보다 낫다.

	비록 하지 않는 것이 종종 지금 *당장* 하는 것보다 나을지라도.

	구현한 것이 설명하기 어렵다면, 그것은 나쁜 아이디어다.

	구현한 것이 설명하기 쉽다면, 그것은 좋은 아이디어일 것이다.

	네임스페이스는 정말 좋은 아이디어다. 더 많이 사용하자!

---

# 2장 파이 재료: 숫자, 문자열, 변수

파이썬에 문자열, 데이터 구조, 함수, 프로그램) 이 **객체**로 구현되어 있다.

파이썬은 객체의 타입을 바꿀 수 없는 **강타입**

변수 이름은 숫자로 시작 할 수 없다.

파이썬의 예약어로 변수를 선언하면 안된다.

- `False` `class` `finally` `is` `return` `None` `continue` `for` `lambda` `try`

- `True` `def` `from` `nonlocal` `while` `and` `del` `global` `not` `with`

- `as` `elif` `if` `or` `yield` `assert` `else` `import` `pass` `break`

- `except` `in` `raise`

- 이 단어들은 파이썬 구문을 정의하는데 사용된다.

### 숫자

0을 다른 숫자 앞에 넣을 수는 없다.

- 05

음수를 표현하려면 숫자 앞에 -기호를 붙인다

- -123

숫자와 연산자 사이의 공백에 상관없이 게산 수행

나눗셈

- `/` 는 **부동소수점**을 포함한 결과가 출력

- `//` 는 부동소수점을 제외한 결과, 즉 **정수**가 출력

- 0으로 나누면 에외 발생

% 문자는 두 숫자 사이의 값을 구할 때 첫 번째 숫자(피제수)를 두 번째 숫자(제수)로 나눈 나머지가 계산된다.

- divmod함수에서 인자로 사용 가능

- divmod(9,5)

	9 % 5
		4

곱셈은 덧셈보다 높은 **우선순위**를 가짐

단일 인용 부호의 문자열을 이중 인용 부호에 넣거나, 이중 이용 부호의 문자열을 단일 인용 부호에 넣을 수 있다.
	"'Nay, ' said the naysayer."
		"'Nay, ' said the naysayer."
	'The rare double quote in captivity: ".'
		'The rare double quote in captivity: "/.'

세 개의 단일 인용 부호혹은 세 개의 이중 인용 부호를 사용할 수 있다.

	''Boom!'''
		'Boom'
	"""Eek!"""
		'Eek!'

`print()` 의 출력 결과와 대화식 인터프리터의 자동 출력 결과는 다름

- `print()` 문자열 인용 부호를 제거한 뒤 내용을 출력

이스케이프 시퀀스 `/t` 는 (tab) 의미

문자열에서 `\'` 혹은 `\"` 을 사용하여v 단일 또는 이중 인용 부호를 표현 할 수 있다.

	test = "\" test!! \"
	print(test)
		"test!!"

백슬래시를 입력하고 싶은 경우에는 백슬러시를 두번 입력 `\\`

문자열 변수가 아닌 **리터럴 문자열**을 결합할 수 있다.
	"test!" "hello"
		'test! hello'

문자열은 불변하기 때문에 특정 인덱스에 문자를 삽입하거나 변경할 수 없다.

	name = 'Hyewon'
	name[0] = 'E'
	Traceback (most recent call last):
	  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/code.py", line 91, in runcode
	    exec(code, self.locals)
	  File "<input>", line 1, in <module>
	TypeError: 'str' object does not support item assignment

**슬라이스**를 사용하여 한 문자열에서 **문자열 일부**를 추출할 수 있다.

**[start:end:step]**

- `[:]` 처음부터 끝까지 전체 시퀀스를 추출

- `[start"]` start 오프셋부터 끝까지 시퀀스를 추출

- `[:end` 처음부터 (end -1) 오프셋까지 시퀀스를 추출

- `[start: end]` start 오프셋 부터 (end -1) 오프셋까지 시퀀스를 추출

- `[start:end:step]` step만큼 문자를 건너뛰면서, start 오프셋부터 (end -1) 오프셋까지 시퀀스를 추출

첫 번째 단어 대문자로 변경

`string.captitalize()`

모든 단어의 첫 글자를 대문자로 변경

`string.title()`

글자 모두 대문자로 변경

`string.upper()`

글자 모두 소문자로 변경

`string.lower()`

대문자는 소문자로, 소문자는 대문자로 변경

`string.swqpcase()`

문자열의 일부를 대체하기 위해서 `replace()` 사용

- replace(인자로 바꿀 문자열, 대체할 새 문자열, 바꿀 문자열에 대한 횟수)
--- 

# 3장. 파이 채우기: 리스트, 튜플, 딕셔너리, 셋

### 슬라이스로 항목추출하기

	슬라이스에 스텝을 사용
	test = ['test1', 'test2', 'test3']
	test[::2]
	['test1', 'test3']
	
	끝에서 왼쪽으로 2칸씩 항목 추출
	test[::-2]
	['test3', 'test1']
	
	리스트 반전
	test[::-1]
	['test3', 'test2', 'test1']

`extend()` 혹은 `+=`를 사용하여 리스트 **병합** 가능

`insert()` 함수를 사용하여 원하는 위치에 항목 추가 가능

	test.insert(1, 'test4')
	test
	['test1', 'test4', 'test2', 'test3']

오프셋으로 항목 삭제하기

	del test[-1]
	test
	['test1', 'test4', 'test2']

**del**

- 리스트 함수가 아니라 파이썬 **구문**

- test[-2].del()을 수행 `X`

- 객체로부터 이름을 분리하고, 객체의 메모리를 비워준다.


`remove()`로 항목 삭제

	test.remove('test2')
	test
	['test1', 'test4']

### 정렬하기 : sort()

`sort()` 는 리스트 자체를 **내부적**으로 정렬

`sorted()`는 리스트의 정렬된 **복사본**을 반환

리스트 항목이 숫자인 경우, 기본적으로 오름차순으로 졍렬

리스트 항목이 문자열인 경우, 알파벳순으로 정렬

### 튜플

	하나 이상의 요소가 있는 튜플은 각 요소 뒤에 콤마(,)를 붙임
	test = '1',
		('1',)
	
	두 개 이상의 요소가 있을 경우, 마지막 요소에는 콤마를 붙이지 않음
	test = '1', '2', '3'
		('1', '2', '3')

**튜플 언패킹**

	한 번에 여러 번슈를 할당
	tuple = 'test', 'test2', 'test3'
	tuple
		('test', 'test2', 'test3')
	a, b, c = tuple
	a
		'test'
	b
		'test2'
	c
		'test3'

왜 튜플을 사용할까? 

- 튜플은 더 적은 공간을 사용

- 실수로 튜플의 항목이 손상될 염려가 없음

- 튜플을 딕셔너리 키로 사용할 수 있다.

- 네임드 튜플은 객체의 단순한 대안이 될 수 있다.

- 함수의 인자들은 튜플로 전달된다.

### 딕셔너리로 변환하기: dict()

	두 항목의 리스트
	test1 = [['a','b'], ['c', 'd']]
		dict(test1)
		{'a': 'b', 'c': 'd'}

	튜플로 된 리스트
	test2 = [('a', 'b'), ('c', 'd')]
		dict(test2)
		{'a': 'b', 'c': 'd'}
	
	리스트로 된 튜플
	test3 = (['a', 'b'], ['c','d'])
		dict(test3)
		{'a': 'b', 'c': 'd'}
	
	두 문자 문자열로된 리스트
	test4 = ['ab', 'cd']
		dict(test4)
		{'a': 'b', 'c': 'd'}
	
	두 문자 문자열로된 튜플
	
	test5 = ('ab', 'cd')
		dict(test5)
		{'a': 'b', 'c': 'd'}

### 딕셔너리 모든 쌍의 키-값 얻기: items()

	list(dict(test5).items())
		[('a', 'b'), ('c', 'd')]

### 딕셔너리 할당:=, 복사: copy()

	딕셔너리를 할당한 후 변경할 때 딕셔너리를 참조하는 모든 이름에 변경된 딕셔너리를 반영
	dict_test = {'test': '1', 'test2':'2'}
	save_test = dict_test
	dict_test['test3'] = '3'
	save_test
		{'test': '1', 'test2': '2', 'test3': '3'}
	
	딕셔너리의 키와 값을 또 다른 딕셔너리로 복사하기 위해서는 위와 같이 할당하지 않고 copy() 사용
	copy_test = dict_test.copy()
	dict_test['test5'] = 5
	copy_test
		{'test': '1', 'test2': '2', 'test3': '3', 'test4': '4'}

### 셋

`셋`은 값을 버리고 키만 남은 딕셔너리

각 키는 유일해야 한다.

어떤 것이 존재하는지 여부만 판단하기 위해 셋을 사용 

### 데이터 타입 변환하기: set()

	'tttest' 셋에는 이 문자들이 하나 씩 포함
	set('tttest')
		{'e', 't', 's'}
	
	리스트를 셋으로 만들기
	set(['test', 'test2', 'test3'])
		{'test3', 'test2', 'test'}
	
	튜플을 셋으로 만들기
	set(('test', 'test1', 'test2'))
		{'test2', 'test', 'test1'}
	
	딕셔너리에 set()을 사용하면 키만 사용된다.
	set({'test':'1', 'test2':'2'})
		{'test2', 'test'}

### 콤비네이션과 연산자

**셋 인터섹션 연산자**(셋 교집합 연산자)인 앰퍼샌트(&)를 사용

	test = {
	    'a': {'test','test2'},
	    'b': {'test1', 'test2', 'test3'}
	    'c': {'test3'}
	}
	for name, contents in test.items():
	    if contents & {'test1', 'test2'}:
	        print(name)

**인터섹션**(교집합: 양쪽 셋에 모두 들어 있는 멤버)

	a = {1,2}
	b = {2,3}
	a & b
		{2}
	
	a.intersection(b)
		{2}

**유니온**(합집합: 각 셋의 멤버 모두)

	a | b
		{1, 2, 3}
	a.union(b)
		{1, 2, 3}

**디퍼런스**(차집합: 첫 번째 셋에는 있지만 두 번째 셋에는 없는 멤버)

	a - b
		{1}
	a.difference(b)
		{1}

**익스클루시브**(대칭 차집합: 한쪽 셋에는 들어 있지만 양쪽 모두에 들어 있지 않은 멤버)

	a ^ b
		{1, 3}
	a.symmetric_difference(b)
		{1, 3}

**부분집합**첫 번째 셋이 두 번째 셋의 서브셋

	a <= b
		False
	a.issubset(b)
		False
	a <= a
		True

첫 번째 셋이 두 번째 셋의 **프로퍼 서브셋**(진부분집합)이 되려면,

두 번째 셋에는 첫 번째 셋의 모든 멤버를 포함한 그 이상의 멤버가 있어야 한다.

	a < b
		False
	a < a
		False

**슈퍼셋**은 서브셋의 반대

	a.issubset(b)
		False
	
	모든 셋은 자신의 슈퍼셋이다
	a >= a
		True
	a.issuperset(a)
		True

첫 번째 셋이 두 번째 셋의 **프로퍼 슈퍼셋**인지 확인

첫 번째 셋이 두 번째 셋의 프로퍼 슈퍼셋이 되려면, 

첫 번째 셋에는 두 번째 셋의 모든 멤버를 포함한 그 이상의 멤버가 있어야한다.

	a > b
		False
	
	모든 셋은 자신의 프로퍼 슈퍼셋이 될 수 없다.
	a > a
		False
--- 
# 4장. 파이 크러스트: 코드 구조
### break 확인하기: else

- while 문이 모두 실행되었지만 발견하지 못했을 경우에는 else가 실행

- for 문에서 break 문이 호출되지 않으면 else 문이 실행

### 여러 시퀀스 순회하기: zip()

`zip()` 함수를 사용하여 여러 시퀀스를 병렬로 순회

- 여러 시퀀스 중 가장 짧은 시퀀스가 완료되면 `zip()` 은 멈춤

- 아래의 예제에서는 리스트 중 하나(dessert)가 다른 리스트보다 길다.

- 그래서 다른 리스트를 모두 확장하지 않는 한 `pudding`을 얻을 수 없다.


	days =['Monday', 'Tuesday', 'Wednesday']
	fruits = ['banana', 'orange', 'peach']
	drintk = ['coffe', 'tea', 'beeer']
	dessert = ['tiramisu', 'ice cream', 'pie', 'pudding']
	
	for days, fruits, drintk, dessert in zip(days, fruits, drintk, dessert):
	    print(days, ": drink", drintk, "-eat", fruits, "-enjoy", dessert)
	
	Monday : drink coffe -eat banana -enjoy tiramisu
	Tuesday : drink tea -eat orange -enjoy ice cream
	Wednesday : drink beeer -eat peach -enjoy pie

`zip()`  함수로 여러 시퀀스를 순회하며, 동일한 오프셋에 있는 항목으로부터 튜플을 만들 수 있다.

	english =  'Monday', 'Tuesday', 'Wednesday'
	french = 'Lundi', 'Mardi', 'Mercredi'
	list(zip(english, french))
	[('Monday', 'Lundi'), ('Tuesday', 'Mardi'), ('Wednesday', 'Mercredi')]
	
	
	zip()의 결과를 dict()에 넣음
	
	dict(zip(english, french))
	{'Monday': 'Lundi', 'Tuesday': 'Mardi', 'Wednesday': 'Mercredi'}

### 컨프리헨션

**컴프리헨션**(comprehension, 함축) 은 하나 이상의 이터레이터로부터 파이썬의 자료구조를 만는 콤팩트한 방법

비교적 간편한 구문으로 반복문과 조건 테스트를 결합할 수 있도록 해준다.(더 파이써닉하게 사용)

**리스트 컴프리헨션**
	[표현식 for 항목 in 순회 가능한 객체]
	
	조건 표현식을 포함할 수 있다.
	[표현식 for 항목 in 순회 가능한 객체 if 조건]
	
	중첩 루프
	rows = range(1,4)
	cols = range(1,3)
	cells = [(row, col) for row in rows for col in cols] 
	cells
	[(1, 1), (1, 2), (2, 1), (2, 2), (3, 1), (3, 2)]
	
	for cell in cells:
	    print(cell)
    	
	(1, 1)
	(1, 2)
	(2, 1)
	(2, 2)
	(3, 1)
	(3, 2)

**딕셔너리 컴프리헨션**
	{키_표현식 : 값_표현식 for 표현식 in 순회 가능한 객체}
	
	word = 'letters'
	letter_counts = {letter: word.count(letter) for letter in word}
	letter_counts
	{'l': 1, 'e': 2, 't': 2, 'r': 1, 's': 1}

위의 예제는 문자열 `letters` 의 각 일곱 글자를 반복해서 글자가 몇 번 나왔는지 그 수를 센다.

`e` 와 `t` 모두 두 번씩 세기 때문에 두 번의 `word.count(letter)` 사용은 시간을 낭비한다.

그러나 두 번째로 `e` 를 셀 때는 딕셔너리에 이미 존재하는 항목을 단지 교체만 하기 때문에 아무런 해가 되지 않음.

	letter_counts = {letter: word.count(letter) for letter in set(word)}
	letter_counts
	{'e': 2, 't': 2, 's': 1, 'r': 1, 'l': 1}

전의 예제와 다르게 정렬되어 있다.

이유는 `set(word)` 를 순회하는 것은 문자열 `word` 를 순회하는 것과 다르게 문자를 반환하기 때문

**셋 컴프리헨션**
	{표현식 for 표현식 in 순회 가능한 객체}
	
	a_set = {number for number in range(1,6) if number % 3 == 1}
	a_set
	{1, 4}

**제너레이터 컴프리헨션**

- **튜플은 컴프리헨션이 없다**

- 아래의 내용은 **제너레이터 컴프리헨션**이며 **제너레이터 객체**를 반환


	number_thing = (number for number in range(1,6))
	
	type(number_thing)
	<class 'generator'>
	
	
	제너레이터 객체를 바로 순환할 수 있다.
	
	for number in number_thing:
	    print(number)
    	
	1
	2
	3
	4
	5
	
	리스트 컴프리헨션처럼 만들기 위해 제너레이터 컴프리헨션에 list() 호출을 랩핑할 수 있다.
	
	number_list = list(number_thing)
	number_list
	[1, 2, 3, 4, 5]

- 제너레이터는 **한 번**만 실행 될 수 있다.

- 리스트, 셋, 문자열, 딕셔너리는 메모리에 존재하지만, 제너레이터는 **즉석에서 그 값을 생성**하고, **이터레이터를 통해서 한 번에 값을 하나씩 처리**한다.

- 제너레이터는 이 **값을 기억하지 않으므로** 다시 시작하거나 제너레이터를 **백업**할 수 **없다**.


### 함수

함수는 입력 **매개변수**로 모든 타입을 여러 개 취할 수 있다.

함수로 전달한 값을 **인자**라 부른다.

인자와 함수를 호출하면 인자의 값은 함수 내에서 해당하는 **매개변수**에 복사된다.

만약 함수가 명시적으로 return을 호출하지 않으면, 호출자는 반환값으로 None을 얻음

**위치 인자**

순서대로 상응하는 매개변수에 복사하는 위치 인자.

**키워드 인자**

매개변수에 상응하는 이름을 인자에 지정

위치 인자와 키워드 인자로 함수를 호출한다면 위치 인자가 먼저 와야 한다.

### 기본 매개 변수 값 지정하기

호출자가 대응하는 인자를 제공하지 않으면 기본값을 사용.

기본 인자값은 함수가 실행될 때 계산되지 않고, 함수를 **정의**할 때 계산된다.

### 위치 인자 모으기: *

파이썬에는 포인터가 없다. 

`*`를 사용할 때 가변 인자의 이름으로 `args` 를 사용할 필요가 없지만 관용적으로 `args`를 사용한다.

함수의 매개변수에 애스터리스크를 사용할 때, 애프터리스크는 매개변수에 위치인자 변수들을 튜플로 묶는다.
	def print_args(*args):
	    print('Positinal argument tuple:', args)
	
	함수를 인자 없이 호출하면 *args에는 아무것 도 없다.
	print_args()
	Positinal argument tuple: ()
	
	인자를 넣어서 args 튜플을 출력해보자.
	print_args(3,2,1, 'wait!', 'uh...')
	Positinal argument tuple: (3, 2, 1, 'wait!', 'uh...')
### 키워드 인자 모으기: **

키워드 인자를 딕셔너리로 묶기 위해 두 개의 `애스터리스크(**)` 를 사용할 수 있다.

키워드 매개변수의 이름을 `kwargs`로 할 필요는 없지만 관용적으로 `kwargs`를 사용한다.	

	def print_kwargs(**kwargs):
	    print('Keyword arguments:', kwargs)
	
	
	함수 안에 kwargs 딕셔너리가 있다.
	
	print_kwargs(wine='merlot', entree='mutton', desert='macaroon')
	Keyword arguments: {'wine': 'merlot', 'entree': 'mutton', 'desert': 'macaroon'}

위치 매개변수와 *args, **kwargs를 섞어서 사용하려면 이들을 순서대로 배치해야한다.

### 일등 시민: 함수

`모든 것이 객체다` 

함수를 변수에 할당할 수 있고, 

다른 함수에서 이를 인자로 쓸 수 있으며, 

함수에서 이를 반환할 수 있다.

	def answer():
	print(42)
	
	answer()
	42
	
	def run_something(func):
	    func()
	
	run_something함수에 answer 인자를 넣으면 다른 모든 인자와 마찬가지로 이 함수를 데이터 처럼 사용한다
	run_something(answer)
	42

	def add_args(arg1, arg2):
	    print(arg1 + arg2)
    	
	
	세 인자를 취하는 run_something() 함수
	def run_something(func, arg1, arg2):
	    func(arg1, arg2)
	
	run_something()를 호출 할 때, 호출자에 의해 전달된 함수는 func 매개변수에 할당되며
	arg1과 arg2는 인자 목록의 값을 얻고
	인자와 함께 func(arg1, arg2) 함수가 실행된다.
    	
	run_something(add_args, 5, 9)
	14

`*args` `**kwargs` 인자와 결합해서 사용 할 수 있다.

	def sum_args(*args):
	    return sum(args)
	
	def run_with_positional_args(func, *args):
	    return func(*args)
	
	run_with_positional_args(sum_args, 1,2,3,4)
	10

함수를 리스트, 튜플, 셋, 딕셔너리의 요소로 사용할 수 있다.

함수는 불변하기 때문에 딕셔너리 키로도 사용할 수 있다.

### 내부함수

함수 안에 또 다른 함수를 정의할 수 있다.

루프나 코드 중복을 피하기 위해 또 다른 함수 내에 어떤 복잡한 작업을 한 번 이상 수행할 때 유용하게 사용된다.

	def outer(a,b):
	    def inner(c,d):
	        return c + d
	    return inner(a, b)
	outer(4,7)
	11

### 클로져

내부함수는 **클로져**처럼 행동할 수 있다.

클로져는 다른 함수에 의해 동적으로 생성된다.

바깥 함수로부터 생성된 변수값을 변경하고, 저장할 수 있는 함수

	innner2()는 인자를 취하지 않고, 외부 함수의 변수를 직접 사용한다.
	knights2() 는 inner2 함수 이름을 호출하지 않고, 이를 반환한다.
	
	def knights2(saying):
	    def inner2():
        	return "We are the knights who say: '%s'" % saying
	    return inner2

`inner2()` 함수는 `knight2()` 함수가 전달받은 `saying` 변수를 알고 있다.

코드에서 return inner2 라인은 (호출되지 않은) inner2 함수의 특별한 복사본을 반환한다.

이것이 외부 함수에 의해 동적으로 생성되고, 그 함수의 변수 값을 알고 있는 함수인 클로져다.

	a = knights2('Duct')
	b = knights2('Hasepfeffer')
	type(a)
	<class 'function'>
	type(a)	
	<class 'function'>
	
	이들은 함수지만, 클로져이기도 하다.
	a
	<function knights2.<locals>.inner2 at 0x1062c7488>
	b
	<function knights2.<locals>.inner2 at 0x1065cdea0>
	
	이들을 호출하면 knights2()함수에 전달되어 사용된 saying을 기억한다.
	a()
	"We are the knights who say: 'Duct'"
	b()
	"We are the knights who say: 'Hasepfeffer'"

### 익명 함수: lambda()
파이썬의 **람다** 함수는 단일문으로 표현되는 익명 함수다.
	words: words 리스트
	func : words의 각각 word 문자열에 적용되는 함수
	
	def edit_story(words, func):
	    for word in words:
	        print(func(word))
	
	stairs = ['thud', 'meow', 'thud', 'hiss']
	
	첫 글자를 대문자로 만들고 느낌표 붙이기
	def enliven(word):
	    return word.capitalize() + '!'
	
	edit_story(stairs,enliven)
	Thud!
	Meow!
	Thud!
	Hiss!

**람다 사용**
	edit_story(stairs, lambda word: word.capitalize() + '!')
	Thud!
	Meow!
	Thud!
	Hiss!

**람다**에서 하나의 word **인자**를 취했다.

람다의 콜론 `(:)` 과 닫는 괄호 사이에 있는 것이 함수의 정의 부분이다.

대부분의 경우 `enliven()` 과 같은 실제 함수를 사용하는 것이 람다를 사용하는 것보다 훨씬 더 명확하다.

람다는 많은 작은 함수를 정의하고,

이들을 호출해서 얻은 모든 결과값을 저장해야 하는 경우에 유용하다.

특히 **콜백 함수**를 정의하는 그래픽 유저 인터페이스(GUI)에서 람다를 사용할 수 있다.

### 제너레이터
- **제너레이터**는 파이썬의 시퀀스를 생성하는 **객체**
- 전체 시퀀스를 한번에 메모리에 생성하고 정렬할 필요 없이,
- 잠재적으로 아주 큰 시퀀스를 **순회**할 수 있다.
- 제너레이터는 **이터레이터에** 대한 **데이터**의 소스로 자주 사용
- 제너레이터는 **순회**할 때마다 **마지막으로 호출된 항목**을 **기억하고 다음 값을 반환**한다.
- 제너레이터는 **일반함수**와 다르다.
- 잠재적으로 큰 **시퀀스를 생성**하고, 제너레이터 **컴프리헨션에 대한 코드**가 긴 경우 **제너레이터 함수를 사용**
- 일반 함수지만 `return`문으로 값을 반환하지 않고, `yield` 문으로 값을 반환

	def my_range(first =0, last=10, step=1):
	    number = first
	    while number < last:
	        yield number
	        number += step
 	
	함수 실행       
	my_range
	<function my_range at 0x109e186a8>
	
	재너레이터 객체를 반환
	ranger = my_range(1,5)
	ranger
	<generator object my_range at 0x109c43f68>
	
	제너레이터 객체를 순회
	for x in ranger:
	    print(x)
	    	
	1
	2
	3
	4

### 데커레이터

**데커레이터**는 하나의 함수를 취해서 또 다른 함수를 반환하는 함수

	def document_it(func):
	    def new_function(*args, **kwargs):
	        print('Running function:', func.__name__)
	        print('Positional arguments:', args)
	        print('Keyword arguments', kwargs)
	        result = func(*args, **kwargs)
	        print('Result:', result)
	        return result
	    return new_function

`document_it()` 함수에 어떤 `func 함수` 이름을 전달하든지 간에 document_it() 함수에 **추가 선언문이 포함된 새 함수**를 얻음

데커레이터는 실제로 `func` 함수로부터 코드를 실행하지 않음

하지만 ducument_it() 함수로 부터 func를 호출하여 **결과 뿐만 아니라 새로운 함수를 얻음**


	def add_ints(a, b):
	    return a + b
	add_ints(3,5)
	8
	
	데커레이터를 수동으로 할당
	cooler_add_ints = document_it(add_ints)
	cooler_add_ints(3,5)
	Running function: add_ints
	Positional arguments: (3, 5)
	Keyword arguments {}
	Result: 8
	8

데코레이터 사용

	@document_it
	def add_ints(a ,b):
	    return a + b
	add_ints(3, 5)
	Running function: add_ints
	Positional arguments: (3, 5)
	Keyword arguments {}
	Result: 8
	8

### 네임스페이스와 스코프
네임스페이스는 **특정 이름**이 유일
다른 네임스페임스에서의 **같은 이름과 관계가 없는 것**
함수로부터 전역변수(global variable)의 값을 얻을 수 있다.

	animal = 'fruitbat'
	def print_global():
	    print('inside print_global', animal)
	    	
	print('at the top level:', animal)
	at the top level: fruitbat
	print_global()
	inside print_global fruitbat

함수에서 전역 변수의 값을 얻어서 바꾸려 하면 에러 발생

	def chage_and_print_global():
	    print('inside change_and_print_global', animal)
	    animal = 'wombat'
	    print('after the change', animal)
	    
	chage_and_print_global()
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	  File "<input>", line 2, in chage_and_print_global
	UnboundLocalError: local variable 'animal' referenced before assignment

함수 내에 있는 지역변수 예제

	def change_local():
		로컬(local) 네임스페이스
		    animal = 'wombat'
		    print('inside change_local', animal, id(animal))
	    
	change_local()
	inside change_local wombat 4461024176

`change_local()` 함수 내의 `animal 변수`가 메인 프로그램의 **animal 변수와 같지 않다는 것을 증명**하기 위해 **파이썬 id()**를 사용
	animal
	'fruitbat'
	id(animal)

함수 내의 `지역 변수(local variable)`가 아닌 전역 변수를 접근하기 위해 `global 키워드`를 사용해서 **전역변수의 접근을 명시**
- 파이썬 철학: **명확한것이 함축적인 것보다 낫다.**

	def change_and_print_global():
	    global animal
	    animal = 'wombat'
	    print('inside change_and_print_global:', animal)
	    
	animal
	'fruitbat'
	
	change_and_print_global()
	inside change_and_print_global: wombat
	animal
	'wombat'

함수 안에 global 키워드를 사용하지 않으면 파이썬은 **로컬 네임스페이스**를 사용하고

변수는 지역 변수가 된다.

**지역 변수는 함수를 수행한 뒤 사라짐**

파이썬은 네임스페이스의 내용을 접근하기 위해 두 가지 함수 제공

	loclas() 함수는 로컬 네임스페이스의 내용이 담긴 딕셔너리를 반환
	globals() 함수는 글로벌 네임스페이스의 내용이 담긴 딕셔너리를 반환

	animal = 'fruitbat'
	def change_local():
			지역변수
	    animal = 'wombat'
	    print('locals:', locals())
	    
	animal
	'fruitbat'
	change_local()
	locals: {'animal': 'wombat'}

### 이름에 _와 __ 사용

두 언더스코어 `(__)` 로 시작하고 끝나는 이름은 파이썬 내의 사용을 위해 **예약**되어 있다.

그러므로 변수를 선언할 때 두 언더스코어를 사용하면 **안 된다**.

애플리케이션 개발자들이 이와 같은 변수 이름을 선택할 가능성이 낮아, 이러한 네이밍 패턴을 선택 한 것

	def amazing():
		'''This is the amazing function.
		Want to see it again?'''
		함수의 이름은 시스템 변수 fuction.__name__
		함수의 doccscring은 function.__doc__
		print('This function is named:', amazing.__name__)
		print('And its docstring is:', amazing.__doc__)
		    
	amazing()
	This function is named: amazing
	And its docstring is: This is the amazing function.

메인 프로그램은 특별한 이름 `__main__` 으로 할당

### 에러 처리하기: try, except

파이썬에서는 관련 에러가 발생할 때 실행되는 코드인 **예외(exception)**를 사용함

	short_list = [1,2,3]
	position = 5
	short_list[positioni]
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	NameError: name 'positioni' is not defined

에러가 발생하도록 코드를 내버려두는 것보다, 에러가 예상되는 코드에 `try문`을 사용하고, 

그 에러를 처리하기 위해 `except문`을 사용

	try:
	    short_list[position]
	except:
	    print('Need a position between 0 and', len(short_list)-1, 'but got', position)
	    
	Need a position between 0 and 2 but got 5

`except` 문을 지정하는 것은 모든 예외타입을 잡는 것

두 개 이상의 예외 타입이 발생하면 각각 별도의 예외 핸들러를 제공하는 것이 가장 좋은 방법

예외 타입을 넘어 예외사항에 대한 **세부정보**를 얻고 싶다면 다음과 같이 **변수** 이름에서 예외 객체 전체를 얻을 수 있다.

`except 예외 타입 as 이름`

---

# 5장. 파이 포장하기: 모듈, 패키지, 프로그램

### 모듈과 impot 문

import 문을 사용하여 다른 모듈의 코드를 참조

이것은 임포트한 모듈의 코드와 변수를 프로그램에서 사용할 수 있게 만들어준다.

import문을 사용하여 간단하게 **모듈**을 임포트 할 수 있다.

모듈은 `.py` 확장자가 없는 파이썬 파일의 이름이다.

코드의 모든 의존성을 명시하기 위해 모든 import문을 파일의 맨 앞에 두는 것을 선호

모듈에 **앨리어스(alias)**를 사용 가능하다

	import reposrt as wr
	wr.함수이름

### 패키지

파이썬 애플리케이션을 좀 더 확장 가능하게 만들기 위해 모듈을 **패키지(package)**라는 파일 계층 구조에 구성할 수 있다.

디렉터리에 `__init__.py` 파일이 필요하다.

이 파일은 내용은 비워도 되지만, 파이썬은 이 파일을 포함하는 디렉터리를 패키지로 간주한다.

### 누락된 키 처리하기: setdefault(), defaultdict()

존재하지 않는 키로 딕셔너리에 접근하려면 예외가 발생

기본값을 반환하는 딕셔너리의 get() 함수를 사용하면 예외를 피할 수 있다.

**setdefault()함수**는 get() 함수와 같지만, 키가 누락된 경우 딕셔너리에 항목을 할당할 수 있다.

	periodic_table = {'Hydrogen':1, 'Helium':2}
	print(periodic_table)
	{'Hydrogen': 1, 'Helium': 2}
	
	딕셔너리에 키가 없는경우 새 값이 사용된다.
	carbon = periodic_table.setdefault('Carbon', 12)
	carbon
	12
	periodic_table
	{'Hydrogen': 1, 'Helium': 2, 'Carbon': 12}

**존재하는** 키에 다른 기본값을 할당하려 하면 키에 대한 원래 값이 반환되고 아무것도 바꾸지 않는다.

	helium = periodic_table.setdefault('Helium', 947)
	helium
	2
	periodic_table
	{'Hydrogen': 1, 'Helium': 2, 'Carbon': 12}

defaultdict() 함수도 비슷하지만 다른 점은 딕셔너리를 생성할 때 모든 새 키에 대한 기본값을 먼저 지정한다.

이 함수의 인자는 함수다.

int()함수를 호출하고 정수 0을 반환하는 함수 int를 전달

	from collections import defaultdict
	periodic_table = defaultdict(int)
	
	periodic_table=['Hydrogen'] = 1
	  File "<input>", line 1
	SyntaxError: can't assign to literal
	periodic_table['Lead']
	0
	periodic_table
	defaultdict(<class 'int'>, {'Lead': 0})

defaultdict()의 인자는 값을 누락된 키에 할당하여 반환하는 함수다.

	def no_idea():
	    return 'Hub?'
	
	bestiary['A'] = 'Abominable snowman'
	bestiary['B'] = 'Basilisk'
	
	bestiary['A']
	'Abominable snowman'
	bestiary['B']
	'Basilisk'
	
	bestiary['C']
	'Hub?'

빈 기본 값을 반환하기 위해 

`int()` 함수는 `정수 0`

`list()` 함수는 `빈 리스트([])`

`dict()` 함수는 `빈 딕셔너라 ({})`

인자를 입력하지 않으면 새로운 키의 초깃값이 None으로 설정

lamda를 사용하여 인자에 기본값을 만드는 함수를 정의 할 수 있다.

	bestiary = defaultdict(lambda: 'Hub?')
	bestiary['E']
	'Hub?'

카운터를 만들기 위해 아래와 같이 int 함수를 사용할 수 있다.

	food_counter = defaultdict(int)
	for food in ['spam', 'spam', 'eggs', 'spam']:
	    food_counter[food] += 1
	    
	
	for food, count in food_counter.items():
	    print(food,count)
	    
	spam 3
	eggs 1

위의 예제에서 food_counter 딕셔너리가 defaultdict가 아닌 일반 딕셔너리였다면,

파이썬은 딕셔너리 요소의 food_counter[food]를 증가시키려고 할 때마다 예외를 발생시킨다.

딕셔녀리가 초기되지 않았기 때문이다.

예외를 피하려면 다음과 같은 추가 작업이 필요

	dict_counter = {}
	for food in ['spam', 'spam', 'eggs', 'spam']:
	    if not food in dict_counter:
		dict_counter[food] = 0
		dict_counter[food] += 1
		    
	for food, count in dict_counter.items():
	    print(food, count)
	    
	spam 3
	eggs 1

### 항목세기: Counter()

**most_common()**함수는 모든 요소를 내림차순으로 반환 

- 숫자를 입력하는 경우, 그 숫자만큼 상위 요소를 반환

항목을 셀 수 있는 예제

	from collections import Counter
	breakfast = ['spam', 'spam', 'eggs', 'spam']
	breakfast_counter = Counter(breakfast)
	breakfast_counter
	Counter({'spam': 3, 'eggs': 1})
	
	breakfast_counter.most_common()
	[('spam', 3), ('eggs', 1)]
	breakfast_counter.most_common(1)
	[('spam', 3)]
	
	lunch = ['eggs', 'eggs', 'bacon']
	lunch_counter = Counter(lunch)
	lunch_counter
	Counter({'eggs': 2, 'bacon': 1})
	
	+ 연산자를 사용하여 두 카운터를 결함
	breakfast_counter + lunch_counter
	Counter({'spam': 3, 'eggs': 3, 'bacon': 1})
	
	- 연산자를 사용하여 한 카운터에서 다른 카운터를 뺄 수 있다.
	breakfast_counter - lunch_counter
	Counter({'spam': 3})

	인터렉션 연산자 & 를 사용해서 공통된 항목을 얻을 수 있다.
	breakfast_counter & lunch_counter
	Counter({'eggs': 1})
	
	유니온 연산자 | 를 사용하여 모든 항목을 얻을 수 있다.
	breakfast_counter | lunch_counter
	Counter({'spam': 3, 'eggs': 2, 'bacon': 1})
	
	`eggs` 가 다시 두 카운터의 공통항목으로 나왔다.
	유니온 연산에서는 breadfast_counter의 `eggs` 가 추가되지 않고 대신 높은 숫자의 공통 항목을 선택

### 키 정렬하기: OrderedDict()

**OrderDict()** 함수는 키의 추가 순서를 기억

이터레이터로부터 **순서**대로 키값을 반환 

### 스택 + 큐 == 데크

**데크**는 스택과 큐의 기능을 모두 가진 출입구가 양 끝에 있는 큐

데크는 시퀀스의 양 끝으로부터 항목을 추가하거나 삭제할 때 유용하게 쓰인다.

`popleft()` 함수는 데크로부터 왼쪽 끝의 항목을 제거한 후, 그 항목을 반환

`pop()` 함수는 오른쪽 끝의 항목을 제거한 후, 그 항목을 반환

	from collections import deque
	def palindrome(word):
	    dq = deque(word)
	    while len(dq) > 1:
	        if dq.popleft() != dq.pop():
	            return False
	        return True
	   	
	palindrome('racecar')
	True
	palindrome('radar')
	True
	palindrome('halibut')
	False

### 코드 구조 순회하기 : itertools

`itertools`는 특수 목적의 이터레이터 함수를 포함하고 있다.

`for ... in` 루프에서 이터레이터 함수를 호출할 때 함수는 한 번에 한 항목을 반환하고 호출 상태를 기억한다.

**itertools 모듈**은 시간을 단축할 수 있는 조합과 순열에 대한 더 많은 함수를 제공

	chain() 함수는 순회 가능한 인자들을 하나씩 반환
	import itertools
	for item in itertools.chain([1,2], ['a', 'b']):
	    print(item)
	    
	1
	2
	a
	b
	
	cycle() 함수는 인자를 순환하는 무한 이터레이터
	for item in itertools.cycle([1,2[):
	    print(item)
	1
	2
	1
	2
	......
	
	accumulate() 함수는 축척된 값을 계산
	기본적으로 합계를 계산
	for item in itertools.accumulate([1,2,3,4]):
	    print(item)
	    
	1
	3
	6
	10
	
	accumulate() 함수의 두 번째 인자로 함수를 전달하여, 합꼐를 구하는 대신 이 함수를 사용
	이 함수는 두 개의인자를 취하여 하나의 결과를 반환
	축적된 곱을 계산
	for item in itertools.accumulate([1,2,3,4], multiply):
	    print(item)
	    
	1
	2
	6
	24

### 배터리 장착: 다른 파이썬 코드 가져오기

파이썬은 전 세계적으로 써드파티 오픈소스가 있다.

- PyPI
- github
- readthedocs

activestate 사이트에서 작은 코드 예제를 많이 찾을 수 있다.

---
### 객체란 무엇인가?

숫자에서 모듈까지 파이썬의 모든 것이 객체

객체는 데이터(변수, 속성이라고 부름)와 코드(함수, 메섣라고 부름)를 모두 포함

객체를 명사 , 메서드를 동사라고 생각하자.

객체는 각각의 사물을 나타내고, 메서드는 다른 사물과 어떻게 상호작용하는지 정의한다.

모둘과 달리, 객체는 각자 다른 값을 가진 속성의 객체를 동시에 여러 개 생성할 수 있다.

### 클래스 선언하기

커스텀 객체를 생성하기 위해 먼저 class 키워드로 클래스 정의

	class Person():
	    pass
		
	함수처럼 클래스 이름을 호출하여 클래스로부터 객체를 생성할 수 있다.
	someone = Person()

Person() 은 Person 클래스로부터 개별 객체를 생성하고, 

someone의 변수에 이 객체를 할당한다.

파이썬 객체 초기화 메서드 `__init__` 을 포함시킨다.

	아무것도 하지 않는 객체일 뿐
	class Person():
	    def __init__(self):
	        pass
	
	name 매개변수를 초기화 메서드에 추가
	name 매개변수에 문자열을 전달하여 Person 클래스로부터 객체를 생성할 수 있다.
	class Person():
	    	def __init__(self, name):
	        self.name = name

- `__init__()` 은 특별한 메서드 이름이다.

- 이 메서드는 클래스의 정의로부터 객체를 초기화 한다.

- `self`  인자는 객체 자신을 가르킨다.

클래스에서 `__init__()` 을 정의할 때, 첫 번째 매개변수는 `self` 여야한다.

비록 파이썬에서 `self` 는 예약어가 아니지만, 일반적으로 이렇게 사용한다.

	hunter = Person('Elmer Fudd')
	
	print('The mighty hunter:', hunter.name)
	The mighty hunter: Elmer Fudd

위의 코드가 어떻게 동작하는지 살펴본다.

- Person 클래스의 정의를 찾는다.
- 새 객체를 메모리에 초기화(생성)
- 객체의 `__init__` 메서드를 호출
- 새롭게 생성된 객체를 `self` 에 전달
- 인자 ('Elmer Fuud')를 name에 전달
- 객체에 name 값을 저장한다.
- 새로운 객체를 반환한다.
- hunter에 이 객체를 연결한다.

이 새로운 객체는 파이썬의 다른 객체의 생성 과정과 같다.

이 객체는 리스트. 튜플, 딕셔너리, 셋의 요소로 사용할 수 있다.

이 객체를 함수에 인자로 전달할 수 있고, 함수에서 그 결과를 반환할 수 있다.

모든 클래스 정의에서 `__init__` 메서드를 가질 필요는 **없다.**

`__init__` 메서드는 같은 클래스에서 생성된 다른 객체를 구분하기 위해 필요한 다른 뭔가를 수행한다.

### 상속

상속을 이용하면 새로운 클래스는 기존 클래스를 복사하지 않고, 기존 클래스의 모든 코드를 쓸 수 있다.

기존 클래스에 일부를 추가하거나 변경하여 새 클래스를 생성한다. 이것은 코드를 재 사용하는 아주 좋은 방법이다.

기존 클래스의 행동을 오버라이드(재정의)한다.

- 필요한 것만 추가/변경하여 새 클래스를 정의

기존 클래스는 **부모 클래스**, **슈퍼 클래스**, **베이스 클래스**라 부른다.

새 클래스는 **자식 클래스**, **서브 클래스**, **파생된 클래스** 부른다.

이 용어들은 객체 지향 프로그래밍에서 다르게 사용될 수 있다.

	class Car():
	    def exclaim(self):
	        print("I',=m a Car!")
	        
	class Yugo(Car):
	    pass
	
	give_me_a_car = Car()
	give_me_a_yugo = Yugo()
	
	give_me_a_car.exclaim()
	I',=m a Car!
	give_me_a_yugo.exclaim()
	I',=m a Car!
	
	자식 클래스는 부모 클래스를 구체화 한 것 
	
	객체 지향 용어로 **Yugo**는 **Car**다.
	
	give_me_a_yugo 객체는 Yugo 클래스의 인스턴스지만, 또한 Car 클래스가 할 수 있는 어떤 것을 상속받는다.
	
### 메서드 오버라이드

위의 예제에서 Yugo에 대한 exclaim() 메서드를 어떻게 바꾸는지 살펴보자.

	class Yugo(Car):
	    def exclaim(self):
	        print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
	        	
	두 클래스로부터 각각 객체를 생성
	give_me_a_car = Car()
	give_me_a_yugo = Yugo()
	
	각 객체의 exclaim() 메서드를 호출
	give_me_a_car.exclaim()
	I',=m a Car!
	give_me_a_yugo.exclaim()
	I'm a Yugo! Much like a Car, but more Yugo-ish.

이 예제에서 exclaim() 메서드를 오버라이드 했다.

`__init__()` 메서드를 포함한 모든 메서드를 오버라이드 할 수 있다.

### 메서드 추가하기

자식 클래스는 또한 부모 클래스에 없는 메서드를 **추가**할 수 있다.

	위의 예제에서 Yugo 클래스에만 새로운 메서드 need_a_push()를 정의
	class Yugo(Car):
	    def exclaim(self):
	        print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
	    def need_a_push(self):
	        print("A little help here?")
	
	give_me_a_car = Car()
	give_me_a_yugo = Yugo()
	
	Yugo 객체는 need_a_push() 메서드 호출에 대답할 수 있다.
	give_me_a_yugo.need_a_push()
	A little help here?
	
	그러나 제네릭 Car 객체는 need_a_push() 메서드를 호출할 수 없다.
	give_me_a_car.need_a_push()
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	AttributeError: 'Car' object has no attribute 'need_a_push'

Yugo는 Car가 하지 못하는 뭔가를 할 수 있으며, Yugo의 독특한 개성을 나타낼 수 있다.

### 부모에게 도움 받기: super

자식 클래스에서 부모 클래스의 매서드를 호출하고 싶다면 `supper()` 메서드를 사용

	class Person():
	    def __init__(self, name):
	        self.name = name
	
	서브 클래스의 __init__() 메서드에 email 매개변수가 추가되었다.
	class EmailPerson(Person):
	    def __init__(self, name, email):
	        super().__init__(name)
	        self.email = email

자식 클래스에서 `__init__()` 메서드를 정의 하면 부모 클래스의 `__init__()` 매서드를 대체하는 것이기 때문에 더이상 자동으로 부모 클래스의 `__init__()` 메서드가 호출되지 않는다.

그러므로 이것을 명시적으로 호출해야한다.

위의 예제가 어떻게 동작하는지 살펴본다.

- `super()` 메서드는 **부모 클래스(Person)의 정의**를 얻는다.
- `__init__()` 메서드는 `Person.__init__()` 메서드를 호출한다.
- 이 메서드는 `self` 인자를 슈퍼 클래스로 전달하는 역할을 한다.
- 그러므로 슈퍼 클래스에 어떤 선택적 인자를 제공하기만 하면 된다.
- 이 경우 `Person()`에서 받은 인자는 `name`이다.
- `self.email = email` 은 EmailPerson 클래스를 Person 클래스와 다르게 만들어주는새로운 코드다.

EmailPerson 객체를 만들어 보자.

	bob = EmailPerson('Bob', 'test.com')
	
	name과 email 속성에 접근 할 수 있다.
	bob.name
	'Bob'
	bob.email
	'test.com'

왜 자식 클래스에서 다음과 같이 정의하지 않았을까?

	class EmailPerson(Person):
	    def __init__(self, name, email):
	        self.name = name
	        self.email = email

- 위와 같이 정의할 수 있지만, 상속을 사용할 수 없게 된다.
- 일반 Person 객체와 마찬가지로 Person 클래스를 활용하기 위해 `super()`를 사용했다(?)
- `super()` 메서드 사용에 대한 다른 이점이 있다.
- 만약 Person 클래스의 정의가 나중에 바꾸면 Person 클래스로부터 상속받은 EmailPerson 클래스의 속성과 메서드에 변경사항이 반영된다.

### 자신: self

파이선은 적절한 객체의 속성과 메서드를 찾기 위해 `self` 인자를 사용

	car = Car()
	car.exclaim()
	I'm a Car!

- car 객체의 Car 클래스를 찾는다.
- car 객체를 Car 클래스의 exclaim() 메서드의 self 매개 변수에 전달

### get/set 속성값과 프로퍼티

객체 지향 언어에서는 외부로부터 바로 접근할 수 없는 `private` 객체 속성을 지원

프로그래머는 `private` 속성의 값을 읽고 쓰기 위해 `getter` 메서드와 setter 메서드를 사용

파이썬에서는 `getter` 나 `setter` 메서드가 필요 없다.

왜냐하면 모든 속성과 메서드는 `public`이기 때문이다.

만약 속성에 직접 접근하는 것이 부담스럽다면 `getter` 와 `setter` 메서드를 작성할 수 있다.

그러나 파이써닉하게 `프로퍼티(property)`를 사용하자!

hidden_name이라는 속성으로 Duck 클래스를 적용해보는 예제

이 속성을 외부에서 직접 접근하지 못하도록 `getter(get_name())`와 `setter(set_name())` 메서드를 정의

	class Duck():
	    def __init__(self, input_name):
	        self.hidden_name = input_name
		def get_name(self):
		        print('inside the getter')
	        	return self.hidden_name
	    def set_name(self, input_name):
	        print('inside the setter')
	        self.hidden_name = input_name

	property()의 첫 번째 인자는 getter 메서드, 두 번째 인자는 setter 메서드
	name = property(get_name, set_name)

Duck 객체의 name을 참조할 때 get_name() 메서드를 호출해서 hidden_name 값을 반환

	fowl = Duck('Howard')
	fowl.name
	inside the getter
	'Howard'
	
	보통의 getter 메서드처럼 get_name() 메서드를 직접 호출 가능
	
	fowl.get_name()
	inside the getter
	'Howard'
	
	name 속성에 값을 할당하면 set_name() 메서드를 호출
	
	fowl.name = 'Daffy'
	inside the setter
	fowl.name
	inside the getter
	'Daffy'
	
	set_name() 메서드를 여전히 직접 호출할 수 있다.
	
	fowl.set_name('Daffy')
	inside the setter
	fowl.name
	inside the getter
	'Daffy'

프로퍼티를 정의하는 또 다른 방법은 **데커레이터** 사용

- `getter` 메서드 앞에 `@property` 데커레이터 사용
- `setter` 메서드 앞에 `@name.setter` 데커레이터 사용

	class Duck():
	    def __init__(self, input_name):
	        self.hidden_name = input_name
	    @property
	    def name(self):
	        print('inside the getter')
	        return self.hidden_name
	    @name.setter
	    def name(self, input_name):
	        print('inside the setter')
	        self.hidden_name = input_name
	
	fowl = Duck('Howard')
	fowl.name
	inside the getter
	'Howard'
	fowl.name = 'Donald'
	inside the setter
	fowl.name
	inside the getter
	'Donald'

프로퍼티 또 한 **계산된 값** 참조 가능

	class Circle():
	    def __init__(self, radius):
	        self.radius = radius
	    @property
	    def diameter(self):
	        return 2 * self.radius
	    
	radisu 속성의 초깃값으로 Circle 객체를 만듦
	c = Circle(5)
	c.radius
	5
	
	radius와 같은 속성처럼 diameter를 참조 가능
	c.diameter
	10
	
	속성에 대한 settr 프로퍼티를 명시하지 않는다면 외부로부터 이 속성을 설정할 수 없다.
	이것은 읽기 전용이다.
	c.diameter = 20
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	AttributeError: can't set attribute

직접 속성을 접근하는 것보다 프로퍼티를 통해서 접근하면 큰 이점이 있다.

예를 들어 만약 속성의 정의를 바꾸려면 모든 호출자를 수정할 필요 없이 클래스 정의에 있는 코드만 수정하면 된다.

### private 네임 맹글링

파이썬은 클래스 정의 외부에서 볼 수 없도록 하는 속성에 대한 네이밍 컨벤션(namaing convention)이 있다.

위의 예제를 수정해 본다.

	class Duck():
	    def __init__(self, input_name):
	        self.__name = input_name
	    @property
	    def name(self):
	        print('inside the getter')
	        return self.__name
	    @name.setter
	    def name(self, input_name):
	        print('inside the setter')
	        self.__name = input_name
	
	fowl = Duck('Howard')
	fowl.name
	inside the getter
	'Howard'
	fowl.name = 'Donald'
	inside the setter
	fowl.name
	inside the getter
	'Donald'

`__name` 속성을 바로 접근 할 수 없다.

	fowl.__name
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	AttributeError: 'Duck' object has no attribute '__name'

네이밍 컨벤션은 속성을 private로 만들지 않지만, 파이썬은 이 속성이 우연히 외부 코드에서 발견할 수 없도록 이름을 **맹글링(mangling)** 했다.


	fowl._Duck__name
	'Donald'

inside the getter를 출력하지 않았다.

이것이 속성을 완벽하게 보호할 수는 없지만, 네임 맹글링은 속성의 의도적인 직접 접근을 어렵게 만든다.

### 메서드 타입

어떤 데이터(**속성**)와 함수(**메서드**)는 클래스 자신의 일부이고, 

어떤 것은 클래스로부터 생성된 객체의 일부다.

**인스턴스 메서드**

- 클래스 정의에서 메서드의 첫 번째 인자가 `self`라면 이 메서드는 **인스턴스 메서드** 다.
- 일반적은 클래스를 생성할 때의 메서드 타입니다.

인스턴스 메서드의 첫 번째 매개변수는 `self` 고, 파이썬은 이 메서드를 호출할 때 객체를 전달한다.

**클래스 메서드**

- **클래스 메서드**는 클래스 전체에 영향을 미친다.
- 클래스 정의에서 함수에 **@classmethod** 데커레이터 사용
- 첫 번째 매개변수는 클래스 자신이다.
- 파이썬에서는 보통 이 클래스의 매개변수를 `cls` 로 쓴다.
- class는 에약어기 때문에 사용할 수 없다.

	class A():
	    count = 0
	    def __init__(self):
	        A.count += 1
	    def exclaim(self):
	        print("I'm an A!")
	    @classmethod
	    def kids(cls):
	        print("A has", cls.count, "little objects")
	        
	easy_a = A()
	breezy_a = A()
	wheezy_a = A()
	A.kids()
	A has 3 little objects

`self.count(객체 인스턴스 속성)` 를 참조하기보다 **A.coutn(클래스속성)**를 참조했다.

kids() 메서드에서 `A.count`를 사용할 수  있었지만 `cls.count`를 사용했다.

**정적 메서드**

클래스 정의에서 메서드의 세 번째 타입은 클래스나 객체에 영향을 미치지 못한다.

이 메서드는 단지 편의를 위해 존재

**정적 메서드**는 `@staticmethod`  데커레이터가 붙어 있다.

첫 번째 매개변수로 `self`나 `cls`가 **없다**.

	class CoyoteWeapon():
	    @staticmethod
	    def commercial():
	        print('This CoyoteWeapon has been brought to you by Acme')
	        
	CoyoteWeapon.commercial()
	This CoyoteWeapon has been brought to you by Acme

이 메서드를 접근하기 위해 CoyoteWeapon 클래스에서 **객체를 생성할 필요가 없다**.

**매우 클래시(class-y)하다**

### 덕 타이핑

파이썬은 **다형성(polymorphism)**을 느슨하게 구현했다.

이것은 클래스에 상관없이 같은 동작을 다른 객체에 적용할 수 있다는 것

세 Qoute 클래스에서 같은 `__init__()` 이니셜라이저를 사용

클래스에 다음 두 메서드를 추가

- `who()` 메서드는 저장된 person 문자열의 값을 반환
- `says()` 메서드는 특정 구두점과 함께 저장된 words 문자열을 반환

	class Quote():
	    def __init__(self, person, words):
	        self.person = person
	        self.words = words
	    def who(self):
	        return self.person
	    def says(self):
	        return self.words + '.'
	    
	class QuestionQuote(Quote):
	    def says(self):
	        return self.words + '?'
	    
	class ExclamationQuote(Quote):
	    def says(self):
	        return self.words + '!'

QuestionQuote와 ExclamationQuote 클래스에서 초기화 함수를 쓰지 않아,

부모의 `__init__()` 메서드를 호출해서 **인스턴스 변수** `person`과 `words`를 저장한다.

그러므로 **서브클래스** QuestonQuote와 ExclamationQuote에서 생성된 객체의 `self.words`에 접근할 수 있다.

	hunter = Quote('Elmer Fudd', "I'm hunting wabbits")
	print(hunter.who(), 'says:', hunter.says())
	Elmer Fudd says: I'm hunting wabbits.
	
	hunter1 = QuestionQuote('Bugs Bunny', "What's up, doc")
	print(hunter1.who(), 'says:', hunter1.says())
	Bugs Bunny says: What's up, doc?
	
	hunted2 = ExclamationQuote('Daffy Duck', "It's rabbit season")
	print(hunted2.who(), 'says:', hunted2.says())
	Daffy Duck says: It's rabbit season!

세 개의 서로 다른 `says()` 메서드는 세 클래스에 대해 서로 다른 동작을 제공

이것은 객체 지향 언어에서 전통적인 다형성의 특징 

파이썬은 `who()`와 `says()` 메서드를 갖고 있는 **모든** 객체에서 이 메서드들을 실행할 수 있게 해준다.

	class BabblingBrook():
	    def who(self):
	        return 'Brook'
	    def says(self):
	        return 'Babble'
	    
	brook = BabblingBrook()
	def who_says(obj):
	    print(obj.who(), 'says', obj.says())

다양한 객체의 `who()` 와 `says()` 메서드를 실행해보면 brook 객체는 다른 객체와 전혀 관계가 없는 것을 알 수 있다.

	who_says(hunter)
	Elmer Fudd says I'm hunting wabbits.
	
	who_says(hunter1)
	Bugs Bunny says What's up, doc?
	
	who_says(hunted2)
	Daffy Duck says It's rabbit season!

예전부터 이러한 행위를 **덕 타이핑(duck typing)**이라고 불렀다.

- 오리처럼 꽥꽥거리고 걷는다면, 그것은 오리다.

### 특수 메서드

파이썬의 **특수 메서드**를 사용하여 연산자를 사용할 수 있다.

문자열을 비교하는 예제이다.

	class Word():
	    def __init__(self, text):
	        self.text = text
	    def equals(self, word2):
	        return self.text.lower() == word2.text.lower()
	    	
	first = Word('ha')
	second = Word('Ha')
	third = Word('eh')
	
	first.equals(second)
	True
	first.equals(third)
	False

`equal()` 메서드를 특수 이름의 `__eq__()` 메서드로 바꿔보자

	class Word():
	    def __init__(self, text):
	        self.text = text
	    def __eq__(self, word2):
	        return self.text.lower() == word2.text.lower()
	    
	first = Word('ha')
	second = Word('HA')
	third = Word('eh')
	
	first == second
	True
	first == third
	False


특수 메서드에 대해 좀 더 알고 싶다면 파이썬 문서를 참고

### 컴포지션

상속은 자식 클래스가 부모 클래스처럼 행동하고 싶을때 사용하는 좋은 기술이다(자식 is-a 부모).

상속을 사용할 수 있지만, **컴포지션(composition)** 또는 **어그리게이션(aggregation)**의 사용이 더 적절한 경우가 있다**(X has-a Y)**.

- 오리는 조류이지만 (오리 is-a 조류), 꼬리를 갖고 있다(오리 has-a 꼬리).
- 꼬리는 오리에 속하지 않지만 오리의 일부

	class Bill():
	    def __init__(self, description):
	        self.description = description
	        
	class Tail():
	    def __init__(self, length):
	        self.length = length
	        
	class Duck():
	    def __init__(self, bill, tail):
	        self.bill = bill
	        self.tail = tail
	    def about(self):
	        print('This duck has a', self.bill.description, 'bill and a', self.tail.length, 'tail')
	        
	tail = Tail('long')
	bill = Bill('wide orange')
	duck = Duck(bill, tail)
	
	duck.about()
	This duck has a wide orange bill and a long tail

이 오리는 넓은 오랜지색 부리와 긴 꼬리를 가지고 있다.

### 클래스와 객체, 그리고 모듈은 언제 사용할까?

- 비슷한 행동(메서드)을 하지만 내부 상태(속성)가 다른 개별 인스턴스가 필요할때, 객체는 매우 유용
- 클래스는 상속을 지원, 모듈은 상속을 지원하지 않는다.
- 어떤 한 가지 일만 수행한다면 모듈이 가장 좋은 선택
    - 프로그램에서 파이썬 모듈이 참조된 횟수에 상관없이 단 하나의 복사본만 불러온다.

- 여러 함수에 인자로 전달될 수 있는 여러 값을 포함한 변수가 있다면, 클래스를 정의
- 간단한 문제 해결방법을 사용
    - 딕셔너리, 리스트, 튜플은 모듈보다 더 작고, 간단하며, 빠르다
    - 일반적으로 모듈은 클래스보다 더 간단하다.

귀도의 조언

	자료구조를 과하게 엔지니어링 하는 것을 피하라.
 	객체보다 튜플이 낫다(네임드 튜플을 써봐라).
 	
 	getter/setter 함수보다 간단한 필드가 더 낫다.
	내장된 데이터 타입, 숫자, 문자열, 튜플, 리스트, 셋, 딕셔너리를 사용하라.
	또한 데크와 같은 컬렉션 라이브러리를 활용하라.

### 네임드 튜플

네임드 튜플은 튜플의 서브클래스이다.

이름(.name), 위치([offset]) 로 값에 접근할 수 있다.

Duck 클래스를 **네임드 튜플**로, bill 과 tail 을 간단한 문자열 속성으로 변환 

두 인자를 취하는 `namedtuple` 함수를 호출

- 이름
- 스페이스로 구분된 필드 이름의 문자열

	from collections import namedtuple
	Duck = namedtuple('Duck', 'bill tail')
	duck = Duck('wide orange', 'long')
	duck
	Duck(bill='wide orange', tail='long')
	duck.bill
	'wide orange'
	duck.tail
	'long'

딕셔너리에 네임드 튜플을 만들 수 있다

	parts = {'bill': 'wide orange', 'tail':'long'}
	duck2 = Duck(**parts)
	duck2
	Duck(bill='wide orange', tail='long')

`**parts` 는 키워드 인자다.

`parts` 딕셔너리에 키와 값을 추출하여 `Duck()` 의 인자로 제공

다음 예제와 효과가 같다.

	duck2 = Duck(bill='wide orange', tail='long')

네임드 튜플은 불변한다. 하지만 필드를 바꿔서 또 다른 네임드 튜플을 반환 할 수 있다.

딕셔너리는 네임드 튜플이 아니다.

	duck.color = 'green'
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	AttributeError: 'Duck' object has no attribute 'color'

**네임드 튜플의 특징**

- 불변하는 객체처럼 행동한다.
- 객체보다 공간 효율성과 시간 효율성이 더 좋다.
- 딕셔너리 형식의 괄호([]) 대신, 점(.) 표기법으로 속성을 접근할 수 있다.
- 네임드 튜플을 딕셔너리의 키 처럼 쓸 수 있다.

---

# 7장. 데이터 주무르기

### 파이썬3 유니코드 문자열

파이썬 3 문자열은 바이트 배열이 아닌 유니코드 문자열이다.

파이썬 3의 유니코드 문자열은 파이썬 2로부터의 가장 큰 변화

파이썬 3은 일반적인 바이트 문자열과 유니코드 문자를 구별한다.

### UTF-8 인코딩과 디코딩

외부 데이터를 교환할 때는 다음 과정이 필요

- 문자열을 바이트로 **인코딩**
- 바이트를 문자열로 **디코딩**

**UTF-8** 동적 인코딩 형식

- 1 바이트: 아스키코드
- 2 바이트: 키릴 문자르 제외한 대부분의 파생된  라틴어
- 3 바이트: 기본 다국어 평면의 나머지
- 4 바이트: 아시아 언어 및 기호를 포함한 나머지

UTF-8은 파이썬, 리눅스, HTML의 표준 텍스트 인코딩

UTF-8은 빠르고 완전하고 잘 동작한다.

**인코딩**

	snowman = '\u2603'
	
	snowman은 한 문자의 파이썬 유니코드 문자열
	
	len(snowman)
	1

유니코드 문자를 바이트 시퀀스로 인코딩

ds = snowman.encode('utf-8')

	UTF-8 은 가변 길이 인코딩
	이 경우 snowman 유니코드 문자를 인코딩하기 위해 3바이트를 사용
	len(ds)
	3
	
	ds는 바이트 변수기 때문에 len() 은 숫자 3을 반환
	ds
	b'\xe2\x98\x83'

UTF-8 이외의 다른 인코딩도 사용할 수 있다.

하지만 유니코드 문자열을 인코딩할 수 없다면 에러를 얻게 된다.

	ds = snowman.encode('ascii')
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	UnicodeEncodeError: 'ascii' codec can't encode character '\u2603' in position 0: ordinal not in range(128)

`encode()` 함수는 인코딩 예외를 피하기 위해 두 번째 인자를 취한다.

위의 예제에서는 두 번째 인자를 지정하지 않았기 때문에 기본값인 `'strict'` 이 지정되었다. 

- 이는 아스키코드가 아닌 문자가 나타났을 때 `UnicodeEncodeError` 를 발생시킴

	'ignore' 는 알 수 없는 문자를 인코딩 하지 않음
	snowman.encode('ascii', 'ignore')
	b''
	
	'replace' 는 알 수 없는 문자를 "?" 로 대체
	snowman.encode('ascii', 'replace')
	b'?'
	
	'backslashreplace' 는 유니코드 이스케이프 처럼 파이썬 유니코드 문자의 문자열을 만듦
	snowman.encode('ascii', 'backslashreplace')
	b'\\u2603'
	
	'xmlcharrefreplace' 는 유니코드 이스케이프 시퀀스를 출력할 수 있는 문자열을 만듦
	snowman.encode('ascii', 'xmlcharrefreplace')
	b'&#9731;'

**디코딩**

바이트 문자열을 유니코드 문자열로 **디코딩**

외부 소스(파일, 데이터베이스, 웹사이트, 네트워크 API등) 에서 텍스트를 어들 때마다 그것은 바이트 문자열로 인코딩 되어있다.

- 이 소스에서 실제로 사용된 인코딩을 알기 위해, 인코딩 과정을 거꾸로 하여 유니코드 문자열을 얻을 수 있다.
- 문제는 바이트 문자열이 어떻게 인코딩되었는지 말해주지 않음

이 예제는 웹사이트의 문자를 아스키 문자로 예상했는데, 이상한 다른 문자로 되어 있는 경우

	place = 'caf\u00e9'
	place
	'café'
	type(place)
	<class 'str'>
	
	UTF-8 형식의 place_bytes라는 바이트 변수로 인코딩
	place_bytes = place.encode('utf-8')
	place_bytes
	b'caf\xc3\xa9'
	type(place_bytes)
	<class 'bytes'>
	
	place_bytes 는 5바이트로 되어있다.
	첫 3바이트는 UTF-8과 똑같이 표현되는 아스키 문자다.
	그리고 마지막 2바이트에서 e 를 인코팅했다.
	
	place2 = place_bytes.decode('utf-8')
	place2
	'café'
	
	아스키 디코더는 0xc3 바이트 값이 아스키코드에 유효하지 않기 때문에 예외가 발생한다.
	place3 = place_bytes.decode('ascii')
	Traceback (most recent call last):
	  File "<input>", line 1, in <module>
	UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)

### 포맷

**옛 스타일: %**

- 문자열 포매팅의 옜 스타일은 `string % data` 형식
- 문자열 안에 끼워넣을 데이터를 표시하는 형식은 보간 시퀀스다

문자열 내의 `%s` 는 다른 문자열을 끼워 넣는 것을 의미

문자열 안의 `%` 수는 뒤 `%` 뒤의 데이터 항목의 수와 일치해야한다.

여러 데이터 항목은 (cat,weight) 와 같이 **튜플**로 **묶어**야 한다.

	actor = 'hyewon'
	cat = 'Chester'
	weight = 28
	"My wife's favorite actor is %s" % actor
	"My wife's favorite actor is hyewon"
	"Our cat %s weight %s pounds" % (cat, weight)
	'Our cat Chester weight 28 pounds'

### 새로운 스타일의 포매팅: {}와 format

	'{} {} {}' .format(actor, cat, weight)
	'hyewon Chester 28'

옛 스타일의 인자는 문자열에서 `%`가 나타난 순서대로 데이터를 제공하지만

새로운 스타일에서는 아래와 같이 순서를 지정할 수 있다.

	'{2} {0} {1}'.format(cat, actor, weight)
	'28 Chester hyewon'

### 정규 표현식

정규표현식은 임포트 할 수 있는 표준 모듈 `re`로 제공

문자열 **패턴**을 정의하여 소스 문자열과 일치하는지 비교

	'You' 는 패턴이고 'Young Frankenstein'은 확인하고자 하는 문자열 소스 
	match() 는 소스와 패턴의 일치 여부를 확인
	
	result = re.match('You', 'Young Frankenstein')
	
	나중에 패턴 확인을 빠르게 하기 위해 패턴을 먼저 컴파일 할 수 있다.
	youpattern = re.compile('You')
	
	컴파일 된 패턴으로 패턴의 일치 여부를 확인할 수 있다.
	result = youpattern.match('Young Frankenstein')

- `match()`  는 시작부터 일치하는 객체 반환
- `search()` 는 첫 번째 일치하는 객체를 반환
- `findall()` 은 중첩에 상관없이 모두 일치하는 문자열 리스트를 반환
- `split()`은 **패턴**에 맞게 **소스**를 쪼갠 후 문자열 조각의 리스트를 반환
- `sub()` 는 **대체 인자**를 하나 더 받아서, 패턴과 일치하는 모든 **소스** 부분을 **대체 인자**로 변경

- `.` 은 한 문자를 의미
- `*` 는 이전 패턴이 여러개 올 수 있다는 것을 의미, `*` 는 0회 이상의 문자가 올 수 있다는 것을 의미

### 패턴: 특수문자

- 리터럴은 모든 비특수 문자와 일치
- `\n` 을 제외한 하나의 문자
- 0회 이상: `*`
- 0 또는 1회: `?`

### 패턴: 지정자

문자 `^` 와 `$` 는 **앵커**라 부른다.

`^` 는 검색 문자열의 시작위치에,`$` 는 검색 문자열의 마지막 위치에 고정 

`$` 는 가장 마지막에 있는 한 문자와 `.` 을 매칭

더 정확하게 하려면 문자 그대로 매칭하기 위해 `.` 에 이스케이프 문자를 붙여야 한다.

파이썬 문자열에서는 `\b` 는 백스페이스를 의미하지만,

정규식 표현식에서는 단어의 시작 부분을 의미

정규표현식의 패턴을 입력하기 전에 항상 문자  `r` (raw string)을 입력하라.

그러면 파이썬의 이스케이프 문자를 사용할 수 없게 되어 실수로 이스케이프 문자를 사용하여 충돌이 일어나는 것을 피할 수 있다.

	source = '''I wish I may, Iwish Imight Have a dish of fish tonight.'''
	re.findall(r'\bfish', source)
	['fish']

### 패턴: 매칭 결과 지정하기

`math()` 또는 `search()` 를 사용할 때 모든 매칭은 `m.group()` 과 같이 객체 m 으로부터 결과를 반환한다.

만약 패턴을 괄호로 둘러싸는 경우, 매칭은 그 괄호만의 그룹으로 저장된다.

`m.groups()` 를 사용하여 그룹의 튜플을 출력

	m = re.search(r'(. dish\b).*(\bfish)', source)
	m.group()
	'a dish of fish'
	m.groups()
	('a dish', 'fish')

만약 (?< *name* > *expr*) 패턴을 사용한다면, 표현식(*expr*)이 매칭되고, 

그룹 이름(*name*)  의 매칭 내용이 저장된다.

	m = re.search(r'(?P<DISH>. dish\b).*(?P<FISH>\bfish)', source)
	m.group()
	'a dish of fish'
	m.groups()
	('a dish', 'fish')
	m.group('DISH')
	'a dish'
	m.group('FISH')
	'fish'

### 이진 데이터

**바이트**는 바이트의 튜플처럼 불변한다.

**바이트 배열**은 바이트의 리스트처럼 변경 가능하다.

바이트 값은 `b` 로 시작하고, 그 다음에 인용 부호가 따라온다.

인용 부호 안에는 `\x02` 또는 아스키 문자와 같은 16진수 시퀀스가 온다.

파이썬은 16진수 시퀀스나 아스키 문자를 작은 정수로 변환한다.

또한 아스키 문자처럼 유효한 아스키 인코딩의 바이트 배열을 보여준다.

	b'\x61'
	b'a'
	b'\x01abc\xff'
	b'\x01abc\xff'

### 이진 데이터 변환하기: struct

struct를 사용하면 이진 데이터를 파이썬 데이터 구조로 바꾸거나 파이썬 데이터 구조를 이진 데이터로 바꿀 수 있다.

`unpack()` 에서 `>LL` 은 입력한 바이트 시퀀스를 해석하고, 파이썬의 데이터 형식으로 만들어주는 형식 문자열이다. 

- `>` 는 정수가 **빅엔디안(big-endian)** 형식으로 저장되었다는 것을 의미
- 각각의 `L` 은 4바이트의 부호 없는 긴 정수를 지정

struct 모듈의 `pack()` 함수로 파이썬 데이터를 바이트로 변환할 수 있다.

	struct.pack('L', 154)
	b'\x9a\x00\x00\x00\x00\x00\x00\x00'
	struct.pack('>L', 141)
	b'\x00\x00\x00\x8d'

### 바이트/문자열 변환하기: binascii()

표준 binascii 모듈은 이진 데이터와 다양한 문자열 표현(16진수, 64진수, uuencoded 등)을 서로 변환할 수 있는 함수를 제공


# 8장. 흘러가는 데이터
활성화된 프로그램은 데이터 램(RAM)에 저장한다.

램은 아주 빠르지만, 비싸고, 일정한 전력 공급을 필요로 한다.

전원이 꺼질 경우 메모리에 있는 모든 데이터가 사라진다.

디스크 라이브는 램보다 느리지만 용량이 넉넉하고, 비용이 비싸며, 전원이 꺼지더라고 데이터를 유지한다.

프로그래머는 디스크와 같은 비휘발성 장치를 사용하여 데이터를 저장하고 복구할 수 있는 **지속성**이 필요하다.

### 파일 입출력

파일을 읽고 쓰기 전에, 파일을 열어야한다.

*fileobj* = open(*filname*, *mode*)

- *fileobj*는 `open()` 에 의해 반환되는 파일 객체
- *filename*은 파일의 문자열 이름
- *mode*는 파일 타입과 파일로 무엇을 할지 명시하는 문자열

*mode*의 첫 번째 글자는 **작업**을 명시

- r : 파일 읽기
- w : 파일 쓰기 (파일이 존재하지 않으면 파일을 생성하고, 파일이 존재하면 덮어쓴다)
- x : 파일 쓰기(파일이 존재하지 **않을** 경우에만 해당)
- a : 파일 추가하기(파일이 존재하면 파일의 끝에서 부터 쓴다)

*mode*의 두 번째 글자는 파일 타입을 명시

- t(또는 아무것도 명시하지 않음): 텍스트 타입
- b : 이진(binary)  타입

파일을 열고 다 사용했다면, 파일을 **닫아야** 한다.

### 텍스트 파일 쓰기: write()

    poem = '''There was a youmn lady named Bright, Whose speed was far faster than light; She started one day In a relative way, And returned on the previous night.'''
    len(poem)
    150

poem을 relativity 파일에 쓴다.

    fout = open('relativity', 'wt')
    fout.write(poem)
    150
    fout.close()

`write()` 함수는 파일에 쓴 바이트수를 반환.

`write()` 함수는 `print()` 함수처럼 스페이스나 줄바꿈을 추가하지 않는다.

    fout = open('relativity', 'wt')
    print(poem, file=fout)
    fout.close()

기본적으로 `print()` 는 각 인자 뒤에 스페이스를, 끝에 줄바꿈을 추가한다.

이전 예제에서는 relativity파일에 줄바꿈이 추가 되었다.

`print()` 를 `write()` 처럼 작동하려면 `print()` 에 다음 두 인자를 전달한다.

- seq(구분자, 기본값은 스페이즈('')다.)
- end(문자열 끝, 기본값은 줄바꿈('\n')이다.)

    fout = open('relativity', 'wt')
    print(poem, file=fout, sep='', end='')
    fout.close()

파일에 쓸 문자열이 크면 특정 단위(chunk)로 나누어서 파일에 쓴다.

    fout = open('relativity', 'wt')
    size=len(poem)
    offset =0
    chunk=100
    while True:
        if offset > size:
            break
        fout.write(poem[offset:offset+chunk])
        offset += chunk

### 텍스트 파일 읽기: read(), readline(), readlines()

`read()` 함수를 인자 없이 호출하여 한 번에 전체 파일을 읽을 수 있다.

아주 큰 파일을 이와 같이 읽을 때 메모리가 소비될 수 있으므로 주의

    fin = open('relativity', 'rt')
    poem=fin.read()
    fin.close()
    len(poem)
    150

한 번에 얼마만큼 읽을 것인지 크기를 제한할 수 있다.

`read()` 함수가 한 번에 읽을 수 있는 문자수를 제한하려면 최대 문자수를인자ㅗㄹ 입력한다.

    한 번에 100문자를 읽은 뒤 각 chunk 문자열을 poem 문자열에 축하ㅏ여 원본 파일의 문자열을 모두 저장
    poem = ''
    fin = open('relativity', 'rt')
    chunk = 100
    while True:
        fragment = fin.read(chunk)
        if not fragment:
            break
        poem += fragment

파일을 다 읽어서 끝에 도달하면, `read()` 함수는 빈 분자열('')을 반환한다.

이것은 `if not fragment` 에서 `fragment`가 False가 되고, 

결국 not False는 True가 되어 while True 루프를 탈출

또한 `readline()` 함수를 사용하여 파일을 라인 단위로 읽을 수 있다.

텍스트 파일의 빈 라인의 길이는 `1` 이고 `\n` , 

이것을 True로 인식한다.

파일 읽기의 끝에 도달 했을 때 (`read()` 함수처럼) `readline()` 함수 또한 Flase로 간주하는 빈 문자열을 반환

텍스트 파일을 가장 읽기 쉬운 방법은 **이터레이터**를 사용하는 것

이터레이터는 한 번에 한 라인씩 반환.

    poem = ''
    fin = open('relativity', 'rt')
    for line in fin:
        poem += line
        
    fin.close()
    len(poem)
    150

### 이진 파일 쓰기 write()  이진 파일 읽기 read()

**모드**에 `'b'` 를 포함 시키면 파일을 이진 모드로 연다.

이 경우 문자열 대신 바이트를 일고 쓸 수 있다.

    fout = open('file', 'wb')
    
    fin = open('bfile', 'rb')

### 자동으로 파일 닫기: with

열려 있는 파일을 닫지 않았을 때, 파이썬은 이 파일이 더 이상 참조되지 않다는 것을 확인한 뒤 파일을 닫는다.

이것은 함수 안에 파일을 열어놓고 이를 명시적으로 닫지 않더라도 함수가 끝날 때 자동으로 파일이 닫힌다는 것을 의미.

파이썬에서는 파일을 여는 것과 같은 일을 수행하는 **콘텍스트 매니저**가 있다.

	파일을 열 때 with 표현식 as 변수 형식을 사용
	with open('relativity', 'wt') as fout:
	    fout.write(poem)

콘텍스트 매니저 코드 블록의 코드 한 줄이 실행되고 나서(잘 수행되거나, 또는 문제가 있는 경우 예외 발생) 자동으로 파일을 닫아준다.

### **콘텍스트** 매너저

컨텍스트 매니저는 `with` 구문에 쓰일 수 있는 객체의 타입이며, (파이썬의 문법 상으로는 명시적으로 지원하지는 않지만) context manager[2](https://soooprmx.com/archives/4079#fn-4079-pep343) 프로토콜을 준수한다. 컨텍스트 매니저는 다음 두 개의 메소드를 정의하고 있는 것으로 간주한다.

- `__enter__(self)` : `with` 문에 진입하는 시점에 자동으로 호출된다.
- `__exit__(self, type, value, traceback)` : `with` 문이 끝나기 직전에 자동으로 호출된다.

`__exit__()` 메소드가 받는 세 개의 인자는 해당 객체와 연관된 컨텍스트 내에서 예외가 발생되었을 때, 해당 예외에 관한 정보이다. 예외없이 with 구문이 종료되었다면 이 세 인자는 모두 None이 될 것이다.

### 파일 위치 찾기: seek()

파일을 읽고 쓸 때, 파이썬은 파일에서 위치를 추적한다.

`tell()` 함수는 파일의 시작으로부터의 현재 오프셋을 바이트 단위로 반환.

`seek()` 함수는 다른 바이트 오프셋으로 위치를 이동할 수 있다.

이 함수를 사용하면 마지막 바이트를 읽기 위해 처음부터 마지막까지 파일 전체를 읽지 않아도 된다. 

`seek()` 함수의 형식은 seek(*offset*, *origin*) 이며, 다음은 두 번째 인자 *origin*에 대한 설명이다.

- *origin*이 0일 때(기본값), 시작 위치에서 *offset* 바이트 이동
- *origin*이 1일 때, 현재 위치에서 *offset* 바이트 이동
- *origin*이 2일 때, 마지막 위치에서 *offset* 바이트 전 위치로 이동

이 함수들은 이진 파일에서 위치를 이동할 때 아주 유용하게 쓰임

텍스트 파일에서는 아스키코드(한 문자당 1바이트)가 아니라면 오프셋을 계산하기 힘들다.

### 구조화된 텍스트 파일

- 탭 `('\t')`, 콤마 `(',')` , 수직 바 `('|')` 와 같은 문자를 **구분자**(혹은 **분리자**)로 사용
    - 여기에서는 CSV(comma-separated value)를 다룬다.
- 태그를 `'< '와'>'` 로 둘러싼다.
    - 여기서는 XML(eXtensible markup language)과 HTML(HyperText Markup Language)을 다룬다.
- 구두점을 사용한다.
    - 여기에서는 JSON(JavaScript Object Notation)을 다룬다.
- 들여쓰기를 사용한다.
    - 여기서는 YAML(YAML Ain't Markup Language)을 다룬다.('YAML은 마크업 언어가 아니다'라는 뜻이다).
- 프로그램 설정 파일과 같은 여러 가지 형식을 사용

이런 구조화된 파일 형식은 적어도 하나의 파이썬 모듈로 읽고 쓸 수 있다.

### CSV(Comma-Separated Values)

수동으로 CSV 파일을 한 번에 한 라인씩 읽어서, 콤마로 구분된 필드를 분리할 수 있다.

그 결과를 리스트와 딕셔너리 같은 자료구조에 넣을 수 있다.

- 어떤 것은 콤마 대신 수직 바 `(|)` 나 탭 `('t')` 문자를 사용
- 어떤 것은 이스케이프 시퀀스를 사용한다. 만일 필드 내에 구분자를 포함하고 있다면, 전체 필드는 인용부호로 둘러싸여 있거나 일부 **이스케이프 문자**가 앞에 올 수 있다.
- 파일은 운영체제에 따라 줄바꿈 문자가 다르다. 유닉스는 `'\n'` , 마이크로소프트는 `'\r\n'`, 애플은 `'r'` 을 썼지만 현재는 `'n'` 을 사용
- 열(column) 이름이 첫 라인에 올 수 있다.

기본값으로 `reader()` 와 `writer()` 함수를 사용하면, 열은 콤마로 나누어지고, 행은 줄바꿈 문자로 나누어진다.

### XML

구분된 파일은 행(라인)과 열(라인에 속하는 필드)의 2차원 구조로 구성되어 있다.

프로그램간에 자료구조를 교환하기 위해 텍스트를 계층구조, 시퀀스, 셋 또는 다른 자료구조로 인코딩 해야한다.

XML은 가장 잘 알려진 **마크업** 형식이다.

XML은 데이터를 구분하기 위해 **태그**를 사용

	<?xml version="1.0"?>
	<menu>
		<breakfast hours="7-11">
			<item price="$6.00"> breakfast burritos</item>
			<item price="$4.00"> pancakes </item>
		</breakfast>
	</menu>

- 태크는 `<` 문자로 시작한다.
    - menu.xml 의 태그는 menu, breakfast 이다.
- 공백은 무시된다.
- 일반적으로 `<menu>` 와 같은 **시작 태그**는 다른 내용이 따라온다. 그러고 나서 `</menu>` 와 같은 **끝 태그**가 매칭된다.
- 태그 안에 태그를 **중첩**할 수 있다.
    - 예제에서 item 태크는 breakfast 태그의 자식이다. 또 한 이 태그들은 menu 태크의 자식이다.
- 옵션 **속성**은 시작 태그에 나올 수 있다.
    - 예제의 price는 item의 속성이다.
- 태그 **값**을 가질 수 있다.
    - 예제의 각 item은 값을 가진다.
    - 예를 들어 두 번째 breakfast의 item은 pancakes 값을 가진다.
- thing이라는 태그에 값이나 자식이 없다면, `<thing></thing>` 과 같은 시작 태그와 끝 태그가 아닌, <thing/>과 같은 단일 태그로 표현할 수 있다.
- 속성, 값, 자식 태그의 데이터를 어디에 넣을 것인가에 대한 선택은 다소 임의적이다.
    - 예를 들어 마지막 item 태그를 `<item price="$8.00" food="spaghetti"/>` 형식으로 쓸 수 있다.

XMl은 데이터 **피드**와 **메시지** 전송에 많이 쓰임

RSS(Rich Site Summary)와 아톰(Atom) 같은 하위 형식이 있다. 

XML의 두드러진 유연성은 접근성과 능력이 다른 여러 파이썬 라이브러리에 영향을 미쳤다.

XMl을 파싱(해석)하는 간단한 방법은 **ElementTree** 모듈을 사용하는 것이다.

### YAML

JSON과 유사하게 YAML은 키와 값을 가지고 있지만, 날짜와 시간같은 데이터 타입을 더 많이 처리한다.

표준 파이썬 라이브러리는 아직 YAML 처리를 지원하고 있지 않아 `yaml` 이라는 써드파티 라이브러리를 사용

`load()` 는 YAML 무자열을 파이썬 데이터로, `dump()` 는 그 반대의 기능을 수행

	PyYAML은 문자열에서 파이썬 객체를 불러올 수 있으나 위험!
	
	신뢰할 수 없는 YAML을 불러온다면 load() 대신 safe_load()를 사용하라.
	
	아직까지는 항상 safe_load()를 사용하는 것이 좋다.

### 기타 데이터 교환 형식

이진 데이터 교환 형식은 일반적으로 더 간결하고 XML이나 JSON보다 빠르다.

- MsgPack
- Protocol Buffers
- Avro
- Thrift

이들은 이진 형식이기 때문에 텍스트 편집기로 쉽게 편집할 수 없다.

### 직력화하기: pickle

자료구조(객체)를 파일로 저장하는 것을 **직렬화**(serializaion)라고 한다.

JSON 과 같은 평식은 파이썬 프로그램에서 모든 데이터 타입을 직렬화하는 컨버터가 필요하다.

파이썬은 바이너리 형식으로 된 객체를 저장하고 복원할 수 있는 `pickle` 모듈을 제공한다.

`dump()` 로 직렬화(pickle) 

`load()` 로 역직렬화(unpickle)


### 구조화된 이진 파일

일부 파일 형식은 특정 자료구조를 저장하기 위해 설계되었지만, 

관계형 데이터베이스나 NoSQL 데이터베이스는 그렇지 않다.

구조화된 이진 파일에 대해 살펴보자

### 스프레드시트

마이크로소프트 엑셀과 같은 스프레드시트(spreadsheet)는 광범위한 이진 데이터 형식

스프레드시트를 CSV 파일로 저장하면 표준 csv 모듈을 사용하여 이 파일을 읽을 수 있다.

### HDF5(Hierarchical Data Format)

다차원 혹은 계층적 수치 데이터를 위한 이진 데이터 형식 

이것은 주로 아주 큰 데이터 집합(기가바이트 ~ 테라바이트)에 대한 빠른 임의적인 접근이 필요한 과학 분야에 주로사용된다.

HDF5는 쓰기 충돌에 대한 데이터베이스의 보호가 필요하지 않은 웜(WORM: Write Once/Read Many, 디스크에 데이터를 단 한 번만 쓸 수 있고, 그 후에는 데이터가 삭제되지 않도록 보호하는 데이터 저장 기술) 애플리케이션에 적합

### 관계형 데이터베이스

- 다수의 동시 사용자가 데이터에 접근
- 사용자에 대한 데이터 손상으로부터의 보호
- 데이터를 저장하고 검색하는 효율적인 방법
- **스키마**(shema)에 의해 정의된 데이터와 **제약조건**(constraint)에 한정되는 데이터
- 다양한 데이터 타입과의 관계(relationship)를 계산하는 **조인**(join)
- (명령형(imperative) 이기보다는) 서술적인(declarative) 질의 언어: **SQL**(Structured Query Lanaguage)

다양한 종류의 데이터 간의 관계를 **테이블**(table) 형태로 표시하기 때문에 **관계형**이라고 부른다.

### SQL

SQL은 API나 프로토콜이 아니다.

SQL은 **어떤** 결과를 얻기 위해 수행 과정을 나열하는 것이 아닌, **원하는** 결과를 질의하는 서술형 **언어**다.

SQL 질의(query)는 클라이언트에서 데이터베이스 서버로 전송하는 텍스트 문자열이다.

- DDL(Data Definition Language(데이터 정의어)
    - 테이블, 데이터베이스, 사용자에 대한 생성, 삭제, 제약조건(constraint), 권한(permission)을 다룬다.
- DML(Data Mainpulation Language(데이터 조작어)
    - 데이터의 조회, 삽입, 갱신, 삭제를 다룬다.

### NoSQL  데이터 스토어

매우 큰 데이터 집합을 처리하고, 데이터 정의에 대해 좀 더 유연하거나 커스텀 데이터 연산을 지원하기 위해 만들어졌다.

### dbm  형식

dbm형식은 키-값 저장 형식

다양한 설정을 유지하기 위해 웹 브라우저와 같은 애플리케이션에 포함된다.

dbm 데이터베잇느는 다음과 같은 점에서 파이썬의 딕셔너리와 같다

- 키에 값을 할당한다. 이것은 디스크에 있는 데이터베이스에 자동으로 저장된다.
- 키로부터 값을 얻는다.

다음 예제는 `open()` 메서드의 두 번째 인자에서 `'r'` 은 읽기, `'w'` 은 쓰기, `'c'` 는 읽기/쓰기(파일이 존재하지 않을 경우에는 파일 생성)을 뜻한다.

	import dbm
	db = dbm.open('definitions', 'c')

키-값 쌍을 생서하려면 딕셔너리처럼 키에 값을 할당한다.

	db['mustard'] = 'yellow'
	db['keychup'] = 'red'
	db['pesto'] = 'green'
	len(db)
	3
	db['pesto']
	b'green'

데이터베이스를 닫은 다음에 다시 열어서 저장한 값이 있는지 확인

	db.close()
	db = dbm.open('definitions', 'r')
	db['mustard']
	b'yellow'

키와 값은 바이트로 저장된다.

데이터베이스 객체 db를 순회할 순 없지만, `len()` 을 사용하여 키와 수는 얻을 수 있다.

`get()`과 `setdefault()`는 딕셔너리의 함수처럼 작동한다.

### Memcached

인메모리 키-값의 **캐시 서버**다.

주로 데이터베이스 앞단에 놓이거나 웹 서버의 세션 데이터를 저장하는데 사용

데이터는 지속되지 않아서, 이전에 쓴 데이터가 사라질 수 있다.

이것은 캐시서버의 memcached 에 대한 특징

이는 오래된 데이터를 제거하여 메모리 부족을 방지한다.

### Redis

Redis는 **자료구조 서버**다.

Redis 서버에 있는 모든 데이터는 memcached처럼 마모리에 맞아야 한다(디스크에 데이터를 저장할 수 있는 옵션이 있다.)

- 서버의 재시작과 신뢰성을 위해 데이터를 디스크에 저장한다.
- 기존 데이터를 유지한다.
- 간단한 문자열 이상의 자료구조를 제공한다.

Redis 데이터 타입은 파이썬 데이터 타입에 가깝다. 

그래서 Redis 서버는 여러 파이썬 애플리케이션에서 데이터를 공유하기 위한 중개 역할로 매우 유용하다.

---

# 9장. 웹

HTTP로 URL을 요청하고 서버로부터 HTML을 받는다.

**HTTP(Hypertext Transfer Protocol)**

- 요청과 응답을 교환하기 위한 웹 서버와 클라이언트의 명세

**HTML(Hypertext Markup Language)**

- 결과에 대한 표현 형식

**URL(Uniform Resource Locator)**

- 고유의 해당 서버와 자원을 나타내는 방법

### 웹 클라이언트

웹은 클라이언트-서버 시스템

클라이언트는 서버에 대한 **요청**을 만든다.

이 요청은 TCP/IP 커넥션을 열고

HTTP를 통해 URL과 다른 정보들을 보낸다. 

요청에 대한 응답을 받는다.

응답 포맷 또한 HTTP에 의해 정의되어 있다.

응답 포맷은 요청에 대한 상태와 응답 데이터를 포함

가장 잘 알려진 웹 클라이언트는 웹 **브라우저**다.

HTTP의 중요한 점은 **무상태(stateless)**라는 것

웹 브라우저에서 생성된 각 HTTP 커넥션은 모두 독립적이다.

- **캐싱(caching)**
    - 변하지 않는 원격 콘텐츠는 웹 클라이언트에 저장하고, 다시 서버로부터 이 콘텐츠의 다운로드를 피하기 위해 저장된 콘텐츠를 사용
- **세선(seesion)**
    - 쇼핑 웹사이트는 쇼핑 카트(장바구니)의 콘텐츠를 기억해야 한다.
- **인증(suthentication)**
    - 아이디와 비밀번호를 요구하는 사이트는 사용자가 로그인할 때, 이 둘은 기억하여 사용자를 식별한다.

무상태에서 대한 해결책 중 **쿠키(cookie)**가 있다.

- 서버가 클라이언트를 식별할 수 있도록 보내는 정보
- 다시 클라이언트가 서버에 쿠키를 보내, 서버가 클라이언트를 식별할 수 있게 한다.

### 파이썬 표준 웹 라이브러리

http는 모든 클라이언트-서버 HTTP 세부사항을 관리한다.

- client는 클라이언트 부분을 관리
- server는 파이썬 웹 서버를 작성하는데 도움을 줌
- cookies와 cookiesjar는 사이트 방문자의 데이터를 저장하는 쿠기를 관리

urllib는 http 위에서 실행

- request는 클라이언트의 요청을 처리
- response는 서버의 응답을 처리
- parse는 URL을 분석

HTTP의 응답 코드는 수십 개가 있는데, 다섯 가지 범위로 나뉜다

**1.XX(조건부 응답 infomation)**

- 서버는 요청을 받았지만, 클라이언트에 대한 몇 가지 추가 정보가 필요

**2.XX(성공 success)**

- 성공적으로 처리되었다. 200 이외의 모든 성공 코드는 추가사항을 전달

**3.XX(리다이렉션 redirection)**

- 리소스가 이전되어 클라이언트에 새로운 URL을 응답해준다.

**4.XX(클라이언트 에러 client error)**

- 자주 발생하는 404(not found)는 클라이언트 측에 문제가 있음을 나타낸다.

**5.XX(서버 에러 server error)**

- 500은 서버 에러를 나타낸다. 웹 서버와 백엔드 애플리케이션 서버가 연결되어 있지 않다면 502(불량 게이트웨이 bad gateway)를 볼 것

웹 서버는 원하는 포맷으로 테이터를 전송할 수 있다.

`application/json`문자열은 **MIME(Mulitpurpose Internet Mail Extensions)**타입 이다.


### 웹 서버 게이트 웨이 인터페이스

파이썬 웹 개발은 파이썬 웹 애플리케이션과 웹 서버 간의 범용적인 API인 **웹 서버 게이트웨이 인터페이스**(Web Server Gateway Inerface **WSGI**)의 정의에서 시작되었다.

### 프레임워크

웹 서버는  HTTP와 WSGI의 세부사항을 처리한다.

반면 웹 **프레임워크**를 사용한다면 파이썬 코드를 작성하여 강력한 웹사이트를 만들 수 있다.

웹 프레임워크는 최소한 클라이언트의 요청과 서버의 응답을 처리한다.

**라우트(route)**

- URL을 해석하여 해당 서버의 파일이나 파이썬 코드를 찾아준다.

**템플릿(template)**

- 서버 사이드의 데이터를 HTML 페이지에 병합

**인증(authentication) 및 권한(authoriazion)**

- 사용자 이름과 비밀번호, 퍼미션(permissioin)을 처리

**세션(session)**

- 웹 사이트에 방문하는 동안 사용자의 임시 데이터를 유지

### Flask

페이스북 인증과 데이터베이스 연결과 같이 전문적인 웹 개발에 유용한 많은 확장 기능을 지원

사용에 대한 용이성과 풍부한 기능의 균형이 잘 갖춰져 있다.

Flask 패키지는 werkzeug WSGI 라이브러리와 jinja2 템플릿 라이브러리를 포함한다. 

### 비파이썬 웹 서버

제품으로 배포할 때는 빠른 웹 서버로 파이썬을 실행하는것이 좋으며, 일반적으로 다음을 선택한다.

- 아파치(apache)와 mod_wsgi 모듈
- 엔진엑스(nginx)와 uWSGI  앱 서버

**아파치**

웹 서버에 최적화된 WSGI 모듈은 mod_wsgi다.

이 모듈은 아파치 프로세스 안에서 혹은 아파치와 통신하기 위해 분리된 프로세스 안에서 파이썬 코드를 실행한다.

**엔진엑스 웹 서버**

엔진엑스 웹 서버는 파이썬 모듈이 없다.

대신 uWSGI와 같은 별도 WSGI 서버를 사용하여 통신

파이썬 웹 개발을 위해 매우 신속하고, 설정 가능한 플랫폼을 만들어줌

**장고**

장고는 전형적인 CRUD(create, read, update, delete) 웹 페이지를 자동으로 생성하기 위한 ORM(Object-Relation Mapping) 코드를 포함한다.

**web2py**

장고와 비슷한 또 다른 스타일의 웹 프레임워크

**pyramid**

장고와 범위가 비슷

**turbogears**

ORM. 여러 데이터베이스, 다중 템플릿 언어를 지원

**wheezy.web**

성능에 최적화된 새로운 웹 프레임워크.

2012.09에 있었던 테스트 결과에서 다른 파이썬 웹 프레임워크보다 빨랐다.

### 웹 API와 REST

데이터에 접근하려면 웹 브러우저를 사용하여 페이지에 접속하고 데이터를 읽음

웹 사이트 방문자가 마지막으로 방문하고 난 이후, 개발자는 웹사이트에서의 데이터 위치와 스타일을 변경할 수 있음

웹 페이지 대신 웹 애플리케이션 프로그래밍 **인터페이스**(Application Programming Interface **API**)

를 통해서 데이터를 제공

클라이언트는 **URL 요청**(request)으로 서비스에 접근하여, 요청에 대한 상태와 데이터가 들어 있는 응답(response)을 받을 수 있음

**RESTful** 서비스는 다음의 특정 HTTP **동사**(verb)를 사용

**HEAD**

- 실제 데이터가 아닌, 리소스에 대한 정보를 얻어옴.

**GET**

- 서버에서 리소스의 데이터를 검색
- 브라우저에서 사용되는 표준 메서드
- 물음표(?)와 함께 인자들이 따라오는 URL
- 데이터를 생성, 변경, 삭제하는데 사용하면 안됨

**POST**

- 서버의 데이터를 갱신.
- 주로 HTML 폼과 웹 API 에서 사용

**PUT**

- 새로운 리소스를 생성

**DELETE**

- 서버의 데이터 삭제

RESTful  클라이언트는 HTTP 요청 헤더를 사용하여 서버로부터 하나 이상의 콘텐트 타입을 요청할 수 있음

### 크롤링과 스크래핑

다음을 수행하여 수동으로 원하는 내용을 추출

1. 브라우저에 URL을 입력
2. 원격 페이지가 불려올 때까지 기다린다.
3. 원하는 정보를 페이지를 통해서 본다.
4. 어딘가에 이 정보를 기록
5. 다른 정보들도 URL을 입력하여 이 과정을 반복

그러나 이러한 과정의 일부 혹은 전체를 자동화하는 것이 더 좋다.

자동화된 웹 패처(fetcher)는 **크롤러**(crawler) 혹은 **스파이더**(spider)라 부름.

원격 웹 서버에서 콘텐츠를 찾은 후,  **스크래퍼**(scraper)에서 원하는 정보를 찾기 위해 파싱한다.

---

# 10장. 시스템

이 장은 모든 프로그램에 사용되는 **os**(operating system) 모듈은 다양한 시스템 함수를 제공

### 생성하기: open()

	fout = open('oops.txt', 'wt')
	print('Oops, I created a file.', file=fout)
	fout.close()

### 존재여부 확인: exists()

	import os
	os.path.exists('oops.txt')
	True

### 타입 확인하기: isfile()

	name = 'oops.txt'
	os.path.isfile(name)
	True

	os.path.isdir(name)
	False

하나의 `(.)`은 현재 디렉터리를 나타내고, 두 개의 점은 부모(상위) 디렉터리를 나타낸다.

os 모듈은 절대 경로와 상대 경로를 처리하는 많은 함수를 제공

`isabs()` 함수는 인자가절대 경로인지 확인. 실제로 존재하는 파일 이름을 인자에 넣지 않아도 된다.

	os.path.isabs('/big/fake/name')
	True

### 복사하기:copy()

`copy()` 함수는 `shutill` 이라는 다른 모듈에 들어있다.

	import shutil
	shutil.copy('oops.txt', 'ohno.txt')
	'ohno.txt'

`shutil.move()` 함수는 파일을 복사한 후 원본 파일을 삭제한다.

### 이름 바꾸기: rename()

	os.rename('ohno.txt', 'ohwell.txt')

### 연결하기: link(), sysmlink()

유닉스에서 파일은 한 곳에 있지만, **링크**(link)라  불리는 여러 이름을 가질 수 있다.

저수준의 **하드 링크**(hard link)에 주어진 파일을 모두 찾는 것은 쉬운일이 아니다.

**심벌릭 링크**(sysbolic link)는 원본 파일을 새 이름으로 연결

원본 파일과 새 이름의 파일을 한 번에 찾을 수 있도록 해준다.

`link()` 함수는 하드 링크를 생성하고, `symlink()` 함수는 심벌릭 링크를 생성

`islink()` 함수는 파일이 심벌릭 링크인지 확인

	os.link('oops.txt', 'yikes.txt')
	os.path.isfile('yikes.txt')
	True

`oops.txt` 파일의 심벌릭 링크인 새 `jeepers.txt` 파일을 생성해 보자

	os.symlink('oops.txt', 'jeepers.txt')
	os.path.islink('jeepers.txt')
	True


### 퍼미션 바꾸기: chmod()

유닉스 시스템에서 `chmoe()` 는 파일의 퍼미션을 변경

사용자에 대한 읽기, 쓰기, 실행 퍼미션이 있다.

	os.chmod('oops.txt', 0o400)

### 절대 경로 얻기: abspath()

상대 경로를 절대 경로로 만들어준다.

	os.path.abspath('oops.txt')
	'/Users/hyewon/workspace/29cm_api/29cm/oops.txt'

### 심벌릭 링크 경로 얻기: realpath()

`relapath()` 함수를 사용하여 `jeepers.txt` 파일로부터 원본 파일인 `oops.txt`파일의 이름을 얻을 수 있다.

	os.path.realpath('jeepers.txt')
	'/Users/hyewon/workspace/29cm_api/29cm/oops.txt'

### 삭제하기: remove()

`remove()` 함수를 사용하여 삭제

	os.remove('oops.txt')
	os.path.exists('oops.txt')
	False

### 디렉터리

대부분의 **운영체제**에서 파일은 **디렉터리(폴더)**의 계층구조 안에 존재

이러한 모든 파일과 디렉터리의 컨테이너는 **파일시스템**이다.(**볼륨**)

**생성하기 mkdir() :** 디렉터리 생성

**삭제하기 rmkir()**: 디렉터리 삭제

**콘텐츠 나열 listdir()**: 디렉터리 콘텐츠 나열

**현재 디렉터리 바꾸기 chdir()**: 현재 디렉터리에서 다른 디렉터리로 이동, 즉 현재 디렉터리를 바꿀 수 있다.

**일치하는 파일 나열 glob()**: 복잡한 정규표현식이 아닌, 유닉스 쉘 규칙을 사용하여 일치하는 파일이나 디렉터리의 이름을 검색

- 모든 것에 일치: `*`(re 모듈에서의 `.*` 와 같다)
- 한 문자에 일치: `?`
- a, b 혹은 c 문자에 일치: [abc]
- a,b 혹은 c를 제외한 문자에 일치: [!abc]

### 프로그램과 프로세스

하나의 프로그램을 실행할 때, 운영체제는 한 **프로세스**를 생성

프로세스는 운영체제의 **커널**(파일과 네트워크 연결, 사용량 통계 등 핵심 역할 수행) 에서 시스템 리소스(CPU, 메모리, 디스크 공간) 및 자료구조를 사용

한 프로세스는 다른프로세스로부터 독립된 존재

프로세스는 다른 프로세스가 무엇을 하는지 참조하거나 방해할 수 없다.

운영체제는 실행 중인 모든 프로세스를 추적함

각 프로세스에 시간을 조금씩 할애하여 한 프로세스에서 다른 프로세스로 전환

운영체제는 두 가지 목표가 있다.

- 프로세스를 공정하게 실행하여 되도록 많은 프로세스가 실행되게 한다.
- 사용자의 명령을 반응적으로 처리하는 것

### 프로세스 생성하기(1): subprocess

파이썬 표준 라이브러리의 `subprocess` 모듈로 존재하는 다른 프로그램을 시작하거나 멈출 수 있다.

	import subprocess
	ret = subprocess.getoutput('date')
	ret
	'Thu Sep  5 13:36:57 KST 2019'

`getoutput()` 함수의 인자는 완전한 쉘 명령의 문자열이므로 인자, 파이프, I/O 리다이렉션(<,>)등 포함

	ret = subprocess.getoutput('date -u')
	ret
	'Thu Sep  5 04:37:55 UTC 2019'

`date -u` 명령에서 파티프로 `wc`  명령을 연결하면 1줄, 6단어, 29글자를 센다.

	ret = subprocess.getoutput('date -u | wc')
	ret
	'       1       6      29'


`check_output()` 이라는 변형 메서트(variant method)는 명령과 인자의 리스트를 취함

표준 출력으로 문자열이 아닌 바이트 타입을 반환하며, 쉘을 사용하지 않는다.

	ret = subprocess.check_output(['date', '-u'])
	ret
	b'Thu Sep  5 04:40:18 UTC 2019\n'

프로그램의 종료 상태를 표시하려면 `getstatusoutput()`을 사용 

프로그램 상태 코드와 결과를 튜플로 반환

	ret = subprocess.getstatusoutput('date')
	ret
	(0, 'Thu Sep  5 13:41:01 KST 2019')

결과가 아닌 상태 코드만 저장하고 싶다면 `call()` 을 사용

	ret = subprocess.call('date')
	Thu Sep  5 13:41:47 KST 2019
	ret
	0

유닉스 계열에서 상태코드 0은 성공적으로 종료되었다는 것을 의미

`date -u` 는 현재 날짜와 시간을 UTC로 출력

	ret = subprocess.call('date -u', shell=True)
	Thu Sep  5 04:42:59 UTC 2019

명령을 인식할 `shell=True`가 필요

명령을 별도의 문자열로 분할하고, `*` 와 같은 와일드카드 문자를 사용

### 프로세스 생성하기(2): multiprocessing

`multiprocessing` 모듈을 사용하면 파이썬 함수를 별도의 프로세스로 실행하거나 한 프로그램에서 독립적인 여러 프로세스를 실행할 수 있다.

프로그램의 전반적인 시간을 줄이기 위해 하나의 작업을 여러 프로세스에 할당할 수 있다.

내려받은 웹 페이지를 스크래핑하고, 이미지가 크기를 조정하는 것 등에 대한 적압을 여러 프로세스로 수행할 수 있다.

`multiprocessing` 모듈은 프로세스 간의 상호 통신과 모든 프로세스가 끝날 때 까지 기다리는 큐 작업에 포함

### 프로세스 죽이기: terminate()

하나 이상의 프로세스를 생성했고, 

어떠한 이유(프로세스가 루프에 빠져서 무한정 기다리거나 심한 과부화를 일으킬 때)로 하나의 프로세스를 종료하고자 하면 `terminate()` 를 사용

### 달력과 시간

	윤년체크 
	
	import calendar
	calendar.isleap(1900)
	False
	calendar.isleap(1996)
	True
	calendar.isleap(1999)
	False
	calendar.isleap(2000)
	True
	calendar.isleap(2002)
	False

시간 또한 다루기 힘든 문제다.

특히 타임존(time zone 표준시간대)과 일광절약 시간제(daylight saving time 서머타임) 때문에 더 힘들다.

파이썬 표준 라이브러리는 `datetime`, `time` , `calendar` , `dateutil` 등 시간과 날짜에 대한 여러가지 모듈이 있다.

### datetime 모듈

- date: 년, 월, 시
- time: 시, 분, 초, 마이크로초
- datetime: 날짜와 / 시간
- timedelta: 날짜와 / 또는 시간 간격

`datetime` 모듈의 `time` 객체는 하루의 시간을 나타내는데 사용 

컴퓨터는 마이크로초를 정확하게 계산할 수 없다.

마이크로초 측정의 정확성은 하드웨어와 운영체제의 많은 요소에 따라 달라진다.

`datetime` 객체는 날짜와 시간 모두를 포함

### time 모듈

파이썬의 `datetime` 모듈의 `time` 객체와 별도다

절대 시간을 나타내는 한 가지 방법은 어떤 시작점 이후 시간의 초를 세는 것

**에포치** : **유닉스 시간**은 1970년 1월 1일 자정 이후 시간의 초를 사용

에포치는 시스템 간에 날짜와 시간을 교환하는 아주 간단한 방식

	import time
	now = time.time()
	now
	1567659554.638052

`ctime()` 함수를 사용하여 에포치 값을 문자열로 변환할 수 있다.

	time.ctime(now)
	'Thu Sep  5 13:59:14 2019'

각각의 날짜와 시간 요소를 얻기 위해 `time 모듈` 의 `struct_time` 객체를 사용할 수 있다.

`localtime()` 메서드는 시간을 시스템의 표준시간대로, 

`gmtime()` 메서드는 시간을 UTC로 제공

	ime.localtime(now)
	time.struct_time(tm_year=2019, tm_mon=9, tm_mday=5, tm_hour=13, tm_min=59, tm_sec=14, tm_wday=3, tm_yday=248, tm_isdst=0)
	time.gmtime(now)
	time.struct_time(tm_year=2019, tm_mon=9, tm_mday=5, tm_hour=4, tm_min=59, tm_sec=14, tm_wday=3, tm_yday=248, tm_isdst=0)

이와 반대로 `mktime()` 메서드는  `struct_time` 객체를 에포치 초로 변환

	tm = time.localtime(now)
	time.mktime(tm)
	1567659554.0

이 값은 조금 전에 본 `now()`의 에포치값과 정확하게 일치하지 않는다.

`struct_time` 객체는 시간을 초까지만 유지하기 때문

가능하면 표준시간대 대신 **UTC 사용**

UTC는 표준시간대와 독립적인 절대시간

그리고 피할 수 있다면 **일광절약시간은 사용하지 마라.**

- 사용하면 연중 한 시간이 한 번에 사라지고(봄이 앞당겨진다),
- 이 시간이 다른 시간에 두번 발생한다(가을이 늦게 온다).

### 날짜와 시간 읽고 쓰기

`strftime()` 을 사용하면 날짜와 시간을 문자열로 변환할 수 있다.

문자열을 날짜나 시간으로 변환하기 위해 같은 포맷 문자열로 `strptime()` 을 사용

이름은 운영체제의 국제화 설정인 **로케일(locale)**에 따라 다르다.

다른 월, 일의 이름을 출력하려면 `setlocale()` 을 사용하여 로케일을 바꿔야한다.

`setlocale()`의 첫 번째 인자는 날짜와 시간을 위한 `locale.LC_TIME` 이고, 

두 번째는 언어와 국가 약어가 결함된 문자열

`long_country` 에 대한 값

	import locale
	names = locale.locale_alias.keys()
	names
	dict_keys(['a3', 'a3_az', 'a3_az.koic', 'aa_dj', 'aa_er', ...])

### 대체 모듈

표준 라이브러리 모듈이 헷갈리거나 특정 포맷 변환이 부족하다 생각되는 경우, 외부 모듈을 사용할 수 있다.

**arrow** **:** 많은 날짜와 시간 함수를 결합하여 간단한 API를 제공

**dateutile:** 이 모듈은 대부분의 날짜 포맷을 파싱하고, 상대적인 날짜와 시간에 대해서도 처리한다.

**iso8601:** 포맷에 대한 표준 라이브러리의 부족한 부분을 보충

**fileming:** 표준시간대 함수를 제공

---

# 11장. 병행성과 네트워크

여러 장소(**분산 컴퓨팅** 혹은 **네트워킹**)에서 동시에 여러 개의 일(**병행성** concurrency)을 할 수 있다.

**성능(perfomance)**

- 느린요소(component)를 기다리지 않고, 빠른 요소를 바쁘게 유지

**견고함(robustness)**

- 하드웨어 및 소프트웨어의 장애를 피하기 위해 작업을 복제하여 여러 가지 안정적인 방식으로 운영

**간소화(simplicity)**

- 복잡한 작업을 좀 더 이해하기 쉽고, 해결하기 쉬운 여러 작은 작업으로 분해

**커뮤니케이션(communication)**

- 데이터(바이트)를 보내고 싶은 곳에 원격으로 전송하고, 다시 데이터를 수신받는다.

### 병행성

컴퓨터가 일을 수행하면서 뭔가 기다린다면, 보통 다음 두 가지 이유 중 하나다.

**I/O바운드** 

- 대부분 이 경우에 해당
- 컴퓨터의 CPU는 엄청나게 빠르다.
- 메모리보다 몇 백배, 디스크나 네트워크보다 몇 천배 빠르다.

**CPU 바운드**

- 과학이나 그래픽 작업과 같이 **엄청난 계산**이 필요할 때 발생

**동기(synchronous)**

- 한 줄의 장례 행렬처럼, 한 작업은 다른 작업을 따른다.
- 워커들은 접시가 처리될 때까지 기다린 후 다른 워커에 넘겨준다.

**비동기(asynchronous)**

- 작업들이 독립적
- 접시가 다른 속도로 워커 사이에 쌓인다.

충분한 워커가 있고, 이 워커들이 작업을 계속 하는 한, 접시들은 빠르게 처리된다.

### 큐

**FIFO(First In First Out)**

- 먼저 들어온 순서대로 가져간다

일반적으로 큐는 **메시지**를 전달

### 스레드

**스레드**는 한 프로세스 내에서 실행

프로세스의 모든 자원에 접근할 수 있다.

스레드를 사용하려면 프로그램의 모든 코드와 이 프로그램을 사용하는 외부 라이브러리에서 반드시 **스레드-세이프한 코드**를 작성해야한다.

스레드는 전역 데이터가 관여하지 않을 때 유용하고 안전하다.

특히 일부 I/O 작업을 완료할 떄까지 기다리는 시간을 절약하는 데 유용하게 쓰인다.

이러한 경우 각 작업은 완전히 별개의 변수를 가지고 있기 때문에 데이터와 씨름할 필요 없다.

전역 데이터를 변경하기 위해 때때로 스레드를 사용하는 좋은 이유가 있다.

여러 개의 스레드를 사용하는 일반적인 이유는 일부 데이터 작업을 나누기 위해서다.

이 경우 데이터 변경에 대한 확실한 정도를 예상할 수 있다.

데이터를 안전하게 공유하는 일반적인 방법은 스레드에서 변수를 수정하기 전에 소프트웨어  **락(**lock 잠금)을 적용하는 것

이것은 한 스레드에서 변수를 수정하는 동안 다른 스레드의 접근을 막아준다.

다음과 같이 파이썬을 사용할 것을 추천

- I/O 바운드 문제 - 스레드 사용
- CPU  바운드 문제 - 프로세스, 네트워킹, 이벤트 사용

### 그린 스레드와 gevent

`gevent` 라이브러리는 이벤트 기반

보통 명령코드를 작성하고, 이 조각들을 **코루틴**으로 변환

- 코루틴은 다른 함수와 서로 통신하여, 어느 위치에 있는지 파악하고 있는 제너레이터와 같다.

`gevent` 는 블로킹(blocking) 대신 이러한 메커니즘을 사용하기 위해 파이썬의 socket과 같은 많은 표준 객체를 수정한다.

`gevent.spawn()` 은 각각의 `gevent.socket.gethostbyname(host)` 를 실행하기 위해 **greenlet(그린 스레드** 혹은 **마이크로 스레드**라고 알려져 있음)을 생성

`greenlet` 과 일반적인 스레드 차이점은 블록(block)을 하지 않는 것 

만약 한 스레드에서 무슨 일이 발생하여 블록되었다면, `gevent`는 제어를 다른 하나의 `greenlet`으로 바꿈

`gevent.joinall()` 메서드는 생성된 모든 작업이 끝날 때 까지 기다린다.

그리고 호스트네임에 대한 IP 주소를 한 번에 얻게 된다.

`gevent` 버전의 socket  대신 몽키-패치(monkey-path) 함수를 쓸 수 있다.

이 함수는 `gevent` 버전의 모듈을 호출하지 않고, `greenlet`을 사용하기 위해 socket과 같은 표준 모듈을 수정한다.

이것은 `gevent` 에 적용하고 싶은 작업이 있을 때 유용

심지어 `gevent` ㅇ[ 접근할 수 없는 코드에도 적용할 수 있다. 

`gevent` 를 사용하면 잠재적 위험이 있다.

모든 이벤트 기반의 시스템에서, 실행하는 각 코드 단위는 상대적으로 빠르게 처리되어야 한다.

논블로킹(nonblocking)임에도 불구하고 많은 일을 처리해야 하는 코드는 여전히 느리다.

### twisted

`twisted` 는 비동기식 이벤트 기반 네트워킹 프레임워크다

`twisted`는 데이터를 받거나 커넥션을 닫는 것과 같이 이벤트오 ㅏ함수를 연결

이 함수는 이러한 이벤트가 발생할 때 호출된다.

이것은 **콜백** 디자인으로 되어있다.

`twisted` 는 TCP와 UDP 위에서 많은 인터넷 프로토콜을 지원하는 큰 패키지다.
