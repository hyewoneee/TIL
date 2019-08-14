# 도서리뷰 - Introducting Python 처음 시작하는 파이썬

# 목차

- [x] 1장. 파이(Py) 맛보기
- [x] 2장. 파이 재료: 숫자, 문자열, 변수
- [x] 3장. 파이 채우기: 리스트, 튜플, 딕셔너리, 셋
- [x] 4장. 파이 크러스트: 코드 구조
- [ ] 5장. 파이 포장하기: 모듈, 패키지, 프로그램
- [ ] 6장. 객체와클래스
- [ ] 7장. 데이터 주무르기
- [ ] 8장. 흘러가는 데이터
- [ ] 9장. 웹
- [ ] 10장. 시스템
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


