---
title: "HTTP의 GET과 POST 비교"
date: 2019-12-26 08:26:28 -0400
categories: get post httpmethods
---

### GET 과 POST의 차이라고 하면 쉽게 떠올리는 것들

- GET은 주소줄에 값이 ?뒤에 쌍으로 이어붙고 POST는 숨겨져서(body안에) 보내진다.
- GET은 URL에 이어붙기 때문에 길이제한이 있어서 많은양의 데이터는 보내기 어렵고 POST는 많은 양을 보내기에 적합하다.(역시 용량제한은 있다.)
- 즉 http://url/bbslist.html?id=5&pagenum=2 같이 하는 것이 GET방식이고 form을 이용해서 submit을 하는 형태가 POST입니다.
- 추가로 GET은 빠른 요청수행을 위해 캐싱할수 있다.

### GET과 POST의 개념적 차이

> GET은 가져오는 것이고 POST는 수행하는 것이다.

- GET은 서버에서 어떤 데이터를 가져와서 보여주는 용도이다. 게시판의 리스트나 글보기등이 해당. 물론 방문 로그를 남긴다거나 글 읽은 횟수를 올려주는 등의 예외는 존재.
- 값을 가져오는 곳에 GET을 사용해야 하는 큰 이유! Link문제. 예를 들어서 어떤 글을 보고있다면 그 페이지를 전달하기위해 주소창의 url을 복사해서 줄 수 있어야한다. POST를 사용한다면 값이 내부적으로 전달되기 때문에 url만 전달할 수 없다. 글을 저장하는 경우에는 url을 제공할 필요가 없기 때문에 post를 사용해도 상관없다.
- POST는 서버의 값이나 상태를 바꾸기 위해서 사용. 글을 쓰거나 수정하면 디비에 내용이 저장된다. 이런경우에 POST사용
- 대표적인 예 google accelerator 사건

### Idempotent관점에서의 차이

- GET은 Idempotent하도록 설계되었고 POST는 Non-idempotent하게 설계되었다. Idempotent하다는 것은 여러 번 수행되어도 동일한 결과가 나타난다는 것.
- POST를 생성, 수정, 삭제에 활용 할 수 있지만 메소드의 의미적으로는 생성에는 POST, 수정에는 PUT 또는 PATCH, 삭제에는 DELETE가 더 용도에 맞는 메소드이다.

### 부수적인 차이

- 부수적인 차이점을 좀 더 살펴보자면 GET 방식의 요청은 브라우저에서 Caching 할 수 있다. 때문에 POST 방식으로 요청해야 할 것을 보내는 데이터의 크기가 작고 보안적인 문제가 없다는 이유로 GET 방식으로 요청한다면 기존에 caching 되었던 데이터가 응답될 가능성이 존재한다. 때문에 목적에 맞는 기술을 사용해야 하는 것이다.
