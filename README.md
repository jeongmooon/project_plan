# Front End Develop

> https://codesandbox.io/
>
> https://www.w3schools.com/

## 수업 공유 링크

> https://github.com/edu-ministori/addinedu_10
>
> https://codesandbox.io/s/html-css-hc9rd?file=/README.md

## Mark Down 문서

```
- 제목 표시 기호 : # ~ ######
- 목록 : -
- 인용문, 중요 내용 표시 : >
- 코드 블럭 : ` (backtick)
```

## 클라이언트 서버 모델

<img src="https://raw.githubusercontent.com/edu-ministori/addinedu_10/main/summary/images/img.png"></img>

- 사용자가 사용하는 디바이스(클라이언트)와 서비스 회사의 서버 컴퓨터가 일대일로 연결되어 있다는 가상의 구성
- 클라이언트와 서버간의 통신 : Request(요청) / Response(응답) 세트로 구성된 통신
- Request : 클라이언트
  Ex) 브라우저에 주소입력 / 엔터 => 요청
- Response : 서버
  Ex) 요청을 받은 사이트의 정보/데이터를 클라이언트에 전송 => 응답

- 클라이언트 : 사용자가 사용하는 디바이스에서 실행되는 소프트웨어
  Ex) 모바일 앱 / 소프트웨어 / 브라우저(웹앱/웹페이지)
- 서버 : 서비스 제공하는 컴퓨터에서 실행되는 소프트웨어
  Ex) 서버 소프트웨어 : Apache(Linux), IIS(Window Server)

- 웹 개발 : 클라이언트(브라우저) / 서버(Apache, IIS)

- Front End Develop

  - 사용자 기준으로 사용자가 확인 가능한 영역(Front)
  - UI/UX 디자인 / 개발 => Front End Develop
  - 웹 개발
    - 브라우저 통해서 화면 표시
    - 프로그래밍 언어(HTML, CSS, JS) 해석(실행) 시점 : 브라우저에서 해석/실행

- Back End Develop

  - 사용자가 확인 불가능한 영역(Back)
  - 데이터 처리 개발
  - 프로그래밍 언어(Javascript+nodejs, JSP, PHP, Python) 해석(실행) 시점 : 서버에서 해석/실행

- Request / Response 개념 + 실행 시점
  - 클라이언트 Request
  - 서버 Response
    - Front End Develop Source
      - Source 상태 전송 => 브라우저가 해석해서 실행 : Rendering(랜더링)
    - Back End Develop Source
      - Source 를 실행 : Compile / Interprete => 데이터 처리 => 처리된 결과 데이터를 전송
