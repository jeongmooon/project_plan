# HTTP multipart/form-data

## HTTP
- 클라이언트와 서버가 자원을 주고 받는 통신 규약

## 이미지파일 전송
- 이미지 파일은 첨부해서 붙여도 png나 jpg 파일자체가 전송되는 것이아님
- 이미지 파일도 문자로 되어있기에 이것이 HTTP RequestBody에 담아 전송됨
- Content-type필드에 여러가지 타입이 적용이 가능함

## multipart & multipart/form-data
- name : 서버로 보내질 이름
- action : form이 전송되는 url or html 링크
- method : 전송 방법
- autocomlete : 자동완성
- enctype : 
        - 폼데이터가 서버로 제출될 떄, 해당 데이터가 인코딩 되는 방법
        - 이 속성은 method가 post일 경우만 사용 가능

## entype 속성값
### application/x-www-form-urlencoded
    - default 값으로, 모든 문자들을 서버로 보내기전 인코딩됨을 명시

### text/plain
    - 공백문자(space)는 "+"로 변환, 나머지는 인코딩되지 않음

### multipart/form-data
    - 모든 문자를 인코딩안함
    - form으로 파일이나 이미지를 서버 전송할때 사용
    - html,jsp 등등...

## 예제

### 단일 업로드 

- view
```
	<form action="/product/addProduct" method="post" enctype="multipart/form-data">
	    <input tpye="file" name="file" />
	    <button type="submit">보내기</button>
	</form>
```

- server
```
	@PostMapping("/testRequestParam")
	public String testControllerRequestParam(MultipartFile file,@ModelAttribute 도메인객체 변수명) throws Exception {

		String projectPath = System.getProperty("user.dir")+ "\\src\\main\\resources\\static";
		UUID uuid = UUID.randomUUID();
		String fileName = uuid+"_"+file.getOriginalFilename();
		File saveFile = new File(projectPath,fileName);
		
		file.transferTo(saveFile);
		
		//setFileName(fileName);
		//setFilepath()
		
		return "맵핑";
	}

```

### 멀티업로드
- view
```
	<form action="/product/addProduct" method="post" enctype="multipart/form-data">
	    <input tpye="file" name="file" />
	    <button type="submit">보내기</button>
	</form>
```

- server
```

	@RequestMapping(value="addProduct", method = RequestMethod.POST)
	public String addProduct(@ModelAttribute("product") Product product,MultipartHttpServletRequest mRequest) throws Exception{
		System.out.println("/addProduct");

		// 파일 저장된객체 확인하기
		System.out.println("\n\n"+mRequest+"\n\n");
		product.setManuDate(product.getManuDate().replace("-", ""));
		String projectPath = 경로;

		List<MultipartFile> fileList = mRequest.getFiles("file");

		for(MultipartFile mf : fileList) {
			String originName = mf.getOriginalFilename();
			long fileSize = mf.getSize();

			System.out.println("원본이름 : "+ originName);
			System.out.println("파일사이즈 : "+fileSize);

			UUID uuid = UUID.randomUUID();
			String fileName = uuid+"_"+originName;

			File saveFile = new File(projectPath,fileName);
			//파일생성 = 새로운파일(저장경로, 저장하는이름)
			mf.transferTo(saveFile);
			// 파일 저장하기
			product.setFileName(fileName);
		}		

		System.out.println(product);
		productService.addProduct(product);
		return "forward:/product/addProduct.jsp";
	}
```
