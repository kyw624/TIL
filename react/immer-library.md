# 불변성 유지 라이브러리 Immer

`Immer` 사용 시 상태를 업데이트 할 때 불변성을 신경쓰지않고 업데이트해도 `Immer`가 관리를 대신 해준다.

`Immer`를 사용한다고 해서 코드가 무조건 간단해지지는 않는다. 주로 복잡한 구조의 상태에 사용하며,  
오히려 코드가 길어지는 경우도 있다. (객체의 구조가 깊지 않은 경우)

<br />

**설치**

```
$ yarn add immer;
```

<br />

**사용예시**

```js
import produce from "immer";

produce(arg1, arg2);
// arg1: 수정하고 싶은 상태
// arg2: 어떻게 업데이트하고 싶은지 정의하는 함수 (불변성 신경 안써도됨.)
```

<br />

**주의점**

확실히 성능면에서는 `Immer`를 사용하지 않은게 조금 더 빠르지만 데이터가 많지 않다면 큰 차이는 없다.

<br />

**결론**

편의성은 확실하기 때문에 데이터 구조가 복잡해져서 불변성을 유지하며 업데이트하려면 코드가 복잡해지는 상황이 온다면 사용을 권장.  
그러나 무조건 사용하지는 말고 가능하다면 데이터의 구조가 복잡해지는 것을 방지할 것.

**어쩔 수 없을 때, 꼭 필요할 때만 사용!!**

<br />

## **참고**

---

[벨로퍼트와 함께하는 모던 리액트 >> Immer 를 사용한 더 쉬운 불변성 관리](https://react.vlpt.us/basic/23-immer.html)
