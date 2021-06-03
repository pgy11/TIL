# JWT

## 1. What is JWT

- JSON Web Token의 약자

- 전송에 오고가는 클레임을 안전하게 표현하는 방법

  - 클레임은 JSON Web Signature의 `payload`또는 JSON Wen Encryption의 평문에 사용되는 JSON 객체로 인코딩된다. 
  - 위의에서 언급한 내용은 클레임을 디지털 서명이 되거나 메세지 인증 코드 또는 암호화으로 보호된 무결성이 될 수 있다.

  <br/>

- JWT는 Header, Payload, Signature로 구성되어있으며 `.`으로 이들을 구분한다.

  ```
  HEADER.PAYLOAD.SIGNATURE
  ```

  <br/>

## 2. Header

- JWT를 어떻게 검증하는가에 대한 내용을 담고있고 아래와 같이 구성되어있다.

  ```json
  {
      "alg": "ES256",
      "kid": "Key ID"
  }
  ```

  <br/>

- `alg`는 서명 시 사용하는 암호화 알고리즘이고 `kid`는 서명시 사용할 키를 식별하는 값이다.

- 위의 JSON 객체를 문자열로 직렬화하고 UTF-8과 Base64 URL-Safe로 인코딩한다.

<br/>

## Payload

- JWT 내용을 담고 있다.

- Payload에 있는 내용들(속성)을 클레임 셋이라고 부른다.

  - 클레임 셋은 클라이언트 정보, 토큰 생성 날짜를 포함한다.

  - 클라이언트와 서버 간 주고 받기로 한 값들로 구성된다.

  - ```json
    {
        "iss": "userid",
        "iat": "20210603"
    }
    ```

  <br/>

- 위의 JSON 객체를 문자열로 직렬화한다음, Base64 URL-Safe로 인코딩한다.

<br/>

## Signature

- `.`을 구분자로 해서 Header, Payload를 한친 문자열을 서명한 값이다.
- 서명은 Header의 `alg`에 정의된 알고리즘과 비밀키를 이용해 생성하고 Base64 URL-Safe로 인코딩한다.
- Header, Payload, Signature가 구성 완료되면, JWT의 모든 내용을 신뢰 할 수 있게되고, Payload의 값으로 접근 제어나 원하는 처리를 할 수 있게된다.

참고링크: https://meetup.toast.com/posts/239

