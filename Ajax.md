---
layout : post
title : "[react] Axios?"
---

# Axios

리액트는 효율적인 UI구현을 위한 라이브러리다. HTTP Client를 내장하고 있는 Angular와는 다르게, 리액트는 따로 내장 클래스가 존재 안한다.

따라서 리액트는 AJAX를 구현하려면 Javascript 내장객체인 XMLRequest를 사용하거나, 다른 HTTP Client를 사용해야한다.

그러면 어떤 라이버리를 사용하는 것이 좋을까? 리액트와 함께 쓰면 좋은 HTTP Client 라이브러리가 많지만, 지금은 Axios라이브러리를 볼 것 이다.

### AJAX란?

AJAX란, Javascript의 라이브러리중 하나고 비동기식 자바스크립트와 xml의 약자다.
브라우저가 가지고 있는 XMLHttpRequest 객체를 이용해서 전체 페이지를 새로 고치지 않고 페이지의 일부만 데이터를 로드하는 기법이고,
JavaScript를 사용한 비동기식 통신, 클라이언트와 서버간에 XML 데이터를 주고 받는 기술이다.

#### 비동기식 통신이란?

> 비동기식 통신은 웹페이지를 리로드하지 않고 데이터를 불러오는 것으로, 
> Ajax를통해서 서버에 요청 한 후 멈춰 있는 것이 아닌 그 프로그램이 계속 
> 돌아가는 것이다.(병렬느낌)

#### 장점은?

> 페이지 리로드의 경우 전체 리소스를 다시 불러와야 하지만, 다른 코드등을
> 모두 재요청 할 경우 불필요한 리소스 낭비가 발생하지만, 비동기식 통신을
> 이용하면 필요한 부분만 불러와 사용할 수 있는 큰 장점이 있다.


# Axios 추가설명

Axios는 Browser, Node.js를 위한 Promise API를 활용하는 HTTP비동기식 통신 라이브러리다.

### 특징

> - 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 HTTP API사용
> - Promise(ES6) API 사용
> - 요청과 응답 데이터의 변형
> - HTTP 요청 취소 및 요청과 응답을 JSON 형태로 자동 변경

### Axios 사용법

- Axios 다운
- HTTP Methods 확인
    - 보통 Methods API를 백앤드에서 받아옴
    - 이번 [API](https://documenter.postman.com/preview/18192539-6afb5dab-be7b-43fa-a923-3512f109e207?environment=&versionTag=latest&apiName=CURRENT&version=latest&documentationLayout=classic-double-column&right-sidebar=303030&top-bar=FFFFFF&highlight=EF5B25)

#### 사용하기 예시

ex) Client 파일 만들기(자주 쓰기 때문)
```
import axios from "axios"

const client = axios.create();

client.defaults.baseURL =
"통신하는URL";

export default client;
```

ex) 사용할 곳
```
client.(메소드(get,post)).('/URL')
```

## 결론

Axios는 사용하기 편한거 같다.