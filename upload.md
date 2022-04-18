# HTML Form 전송방식

## application/x-www-form-urlencoded
- 폼 데이터를 서버로 전송하는 가장 기본적인 방법
- Form태그에 별도의 enctype옵션이 없다면 HTTP 바디와 함께 전송
- 파일 업로드 하려면 문자가 아닌 바이너리 데이터에 전송해야함

## multipart/form-data
- 파일과 함게 항목을 전송하기 위하여 multipart/form-data라는 방식이 제공된다

```
POST/save HTTP/1.1 Host:localhost:8080 Content-Type:multipart/form-data,boundary=------XXX 

-------XXX Content-Disposition: form-data; name="username" kim 

-------XXX Content-Disposition: form-data; name="age" 20 

-------XXX Content-Disposition: form-dta; name="file"; filename="example.png" Content-Type: image/png (바이너리 코드....) -

------XXX--

```

이런식으로 전송 된다고함

## MultipartFile
- @RequestParam을 업로드하는 HTML Form의 name에 맞춰 적용해야 한다

## **
클라이언트가 Form을 통해 파일을 보내면, 보통 폼에 입력한 항목들을 같이 전송하기 때문에 MultipartForm을 사용하여 보내게 된다. 말 글대로 여러 파트로 구분하여 보내어 지는데 이것을 스프링은 MultipartFile 인터페이스가 지원된다