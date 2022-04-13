---
layout : post
title : "[HTTP] REST"
---

# REST?

Representional State Transfer의 약자이고,

***자원(Resource):URI***,***행위(Verb):HTTP Method***,***표현(Representaions)***로 구성되어 있다. 

REST는 URI를 통해 자원을 표시하고, HTTP Method를 이용해 자원을 규정하여 결과를 받는 것이다.
HTTP Method는 크게 GET, POST, PUT, DELETE가 있으며 CRUD 에서 조회는 GET, 등록은 POST, 수정은 PUT, 삭제는 DELETE를 이용한다.

GET과 DELETE는 행위가 명확한 편이지만, POST와 PUT은 구분하기위해 멱등성을 알아야한다.
멱등성이란, 수학에서는 연산을 여러번 적용하더라도 결과가 달라지지 않는 다는 뜻이다.
이 것은 **'요청의 효과'** 를 보고 판단한다. 서버의 상태는 같은 것을 여러 번 반복하더라도 같은 효과를 가져야 한다.
위에 대표적인 4개의 Method에서 POST를 제외하고 모두 멱등성이 보장되어야 한다.
이는 응답이 다를 수도 있지만, 의도한 효과를 보일 때, 멱등성이 유지되어야 하는걸 의미한다.


### 안전한 메소드란?

안전한 메소드는 GET, HEAD와 같은 서버측의 상태정보를 변경하지 않는 메소드를 말한다
안전한 메소드와 멱등성을 지키는 메소느는 서로 다르다

예를 들면 우리가 데이터를 만들때 POST로 요청을하고, 반복 요청하면 데이터들은 계속 추가되고, 서버는 그때마다 다른응답을 보이고 다른효과를 지닐 것이다.(둘다 아님)

하지만 GET으로 요청을 불러오는 것은 우리가 수십번을 반복해도 서버의 상태가 변하지 않고, 같은효과를 기대 할 수가 있다.(멱등성과 안전한 메소드)

PUT의 경우엔 데이터를 지정하여 수정하고, 지정한 데이터가 없는 경우 생성 될 수 있고, 이미 존재하면, 서버에 저장된 데이터는 수정이 된다. 여러번 실행 하더라도 우리가 요청한 그 값이 항상 수정이 되는 것이다(멱등성이지만 서버가 변해 안전한 메소드는 아님)

DELETE 요청도 PUT과 똑같이 이미 존재하든, 안하든 그데이터는 DELTE를 보낸 시점에 사라지고 우리가 원하는 것이 이루어진다(멱등성이지만 서버가 변해 안전한 메소드는 아님)

## 결론
- 안전한 메소드는 서버의 상태를 아얘 변경시키지 않는다.
- 멱등성을 가진 메소드는 서버의 상태를 변경시킬 수도 있고, 아닐 수도 있다. 하지만 우리가 요청한 사항은 에러가 생기지 않는 이상 요청에 대한 서버 상태는 항상 같다

### 번외? HTTP상태코드 의미

- 200 번대는 성공을 의미한다
- 300 번대는 리다이렉션인데 이 뜻은 location헤더가 있으면 loacation 위치로 자동 이동하는 것을 의미한다.
- 400 번대는 클라이언트가 오류를 발생했다는 것을 알려준다(서버는 문제 x)
- 500 번대는 서버측에서 오류가 발생한 것이다(클라이언트는 문제 x)