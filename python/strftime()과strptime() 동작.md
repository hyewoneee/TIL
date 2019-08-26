### strftime()

`datetime.strftime() 함수 (datetime to str)` 

**date, datetime 및 time 객체**는 모두 strftime(format) 메서드를 지원

**명시적 포맷 문자열로 제어된 시간을 나타내는 문자열**을 만든다.

모든 객체가 timetuple() 메서드를 지원하는 것은 아니지만 d.strftime(fmt)는 time  모듈의 **time.strftime(fmt, d.timetuple())** 처럼 작동한다.

date.isoformat()

- date 객체의 정보를 `YYYY-MM-DD` 형태의 문자열로 변환

### strptime()

`datetime.strptime()  함수 (str to datetime)`

datetime.strptiome() 클래스 **메서드는 날짜와 시간을 나타내는 문자열**과 **해당 포맷 문자열로 datetime 객체**를 만든다.

datetime.strptime(date_string, format)은 format에 초 미만의 성분이나 시간대 오프셋 정보가 포함된 경우를 제외하고는 datetime(*(time.strptime(date_string, format)[0:6]))과 동등하다.

이것들은 **datetime.strptime에서는 지원**되지만 time.strptime에서는 버려진다.

**datetime.strptime()** 클래스 매서드의 경우 기본값은 `19000-01-01T00:00:00` : 포맷 문자열에 지정되지 않은 구성 요소는 기본값에서 가져온다.
