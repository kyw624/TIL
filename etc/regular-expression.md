# 정규 표현식 (RegExp, Regular Expression)

문자열에서 특정 조건의 문자를 검색하거나 치환하는 과정을 매우 간편하게 처리 할 수 있는 방법이다.

<br />

## **문법**

### Groups and ranges

| Character | 뜻                             |
| --------- | ------------------------------ |
| `\|`      | 또는                           |
| `()`      | 그룹에 포함                    |
| `(?:)`    | 찾지만 그룹으로 기억하지 않음  |
| `[]`      | 문자셋 (괄호 안의 문자들 포함) |
| `[^]`     | 부정 문자셋 (문자셋의 not)     |

```js
const str = 'ABCDEF 123456';

str.match(/789|123456/); // '123456'

str.match(/(ABC).+(123)(?:456)/);
/*
찾은 문자와 그룹들이 순서대로 배열로 반환. ?: 사용 시 찾았지만 기억은 안함.
arr = ['ABCDEF 123456', 'ABC', '123']
*/

str.match(/[A-C]/); // 'A'
str.match(/[A-C]+/); // 'ABC'

str.match(/[^A-C]/); // 'D'
str.match(/[^A-C]+/); // 'DEF 123456'
```

<br />

### Quantifiers

| Character   | 뜻                                    |
| ----------- | ------------------------------------- |
| `?`         | 없거나, 있거나 (zero or one)          |
| `*`         | 없거나, 있거나, 많거나 (zero or more) |
| `+`         | 하나 또는 많이 (one or more)          |
| `{n}`       | n번 반복됨                            |
| `{min,}`    | 최소 min개                            |
| `{min,max}` | 최소, 최댓값                          |

```js
const str = 'ABCDEF 123456';
const compare = 'BBBCDEF';

str.match(/A?\w/); // 'AB'
compare.match(/A?\w/); // 'B'

compare.match(/B*/); // 'BBB'
compare.match(/B+/); // 'BBB'

compare.match(/B{2}/); // 'BB'
compare.match(/B{1,}/); // 'BBB'
compare.match(/B{1,2}/); // 'BB'
```

<br />

### Boundary-type

| Character | 뜻                               |
| --------- | -------------------------------- |
| `\b`      | 단어 경계 (공백으로 경계가 나뉨) |
| `\B`      | 단어 경계가 아님 (\b의 반대)     |
| `^`       | 문장의 시작 (`/^reg/`)           |
| `$`       | 문장의 끝 (`/reg$/`)             |

```js
const str = 'ABCDEF 123456';

str.match(/\w{3}\b/); // 'DEF', 중간 공백을 경계로 3글자
str.match(/\b\w{3}/); // 'ABC', 맨 앞을 경계로 3글자

str.match(/^\w/); // 'A'
str.match(/\w$/); // '6'
```

<br />

### Character classes

| Character | 뜻                                          |
| --------- | ------------------------------------------- |
| `\`       | 특수 문자가 아닌 문자 (\. => .을 포함시킴)  |
| `.`       | 어떤 글자 (= 와일드 카드, 줄바꿈 문자 제외) |
| `\d`      | 숫자 (digit)                                |
| `\D`      | 숫자가 아님                                 |
| `\w`      | 문자 (word)                                 |
| `\W`      | 문자가 아님                                 |
| `\s`      | 공백 (space)                                |
| `\S`      | 공백이 아님                                 |

```js
const str = 'ABCDEF 123456 ?/-+';

str.match(/\ /); // ' ' (첫번째 공백)

str.match(/.{4}/); // 'ABCD'

str.match(/\d{4}/); // '1234'
str.match(/\D{4}/); // 'ABCD'

str.match(/\w{4}/); // 'ABCD'
str.match(/\W{4}/); // ' ?/- (앞의 공백부터 4자리)'

str.match(/\s/); // ' ' (첫번째 공백)
str.match(/\S{4}/); // 'ABCD'
```

<br />

## **참고**

---

[드림코딩 by 엘리 유튜브 >> 정규표현식 , 더이상 미루지 말자 🤩](https://www.youtube.com/watch?v=t3M6toIflyQ)  
[정규표현식 연습](regexr.com/5mhou)  
[정규표현식 퀴즈 >> RegexOne](https://regexone.com/)
