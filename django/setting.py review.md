# setting.py review

## 1. `Base_dir`

- `__file__()`은 코드가 있는 파일 경로를 알아내는데 사용하는 특별 메소드

- `setting.py`의 `BASE_DIR`변수는 프로젝트의 최초 진입점을 의미한다.

  - 진행 중인 프로젝트의 경우, `repo`폴더가 `BASE_DIR`이 된다. 

  <br/>

## 2. SECRET_KEY

- `SECRET_KEY`는 해시를 만드는데 사용한다.(참고: https://stackoverflow.com/questions/7382149/whats-the-purpose-of-django-setting-secret-key)
- 공식 문서에 따르면, `SECRET_KEY`는 Cryptographic signing를 제공하는데 사용된다.
- `SECRET_KEY`는 유일하며, 예측할 수 없는 값이다.

<br/>

## 3. ALLOWED_HOSTS

- `ALLOWED_HOST`는 호스트명/도메인명을 표현하는 문자열을 담는 리스트이다.

- HTTP Host header attack을 막기 위한 안전 수단이다.

- `DEBUG = True`이고 `ALLOWED_HOST = []`일 때, 호스트는  `['.localhost', '127.0.0.1', '[::1]']`를 의미한다.

  - `DEBUG = False`일 때, `ALLOWED_HOST`를 명시적으로 지정해야한다.
  - `ALLOWED_HOST=['*']`일 때, 어떠한 호스트명/도메인명과 매칭된다.

  <br/>

## 4. INSTALLED_APP

- 장고 설치에서 활성화된 모든 애플리케이션을 지명하는데 사용하는 문자열 리스트이다.
- 애플리케이션 구성 클래스명, 애플리케이션을 포함하는 패키지명을 작성해야하며, `INSTALLED_APP`에서 유일해야한다.

<br/>

## 5. MIDDLEWARE

- 장고의 요청/응답 처리에 관한 Hook framework
- 장고의 입출력을 전역적으로 바꿔주는 가볍고, 저수준의 플러그인
- 애플리케이션에 제공하는 기능들을 작성한다.

<br/>

## 6. AUTH_PASSWORD_VALIDATORS

- 작성된 비밀번호가 유효한지 검사할 때 사용하는 변수
  - 사용자가 비밀번호를 1자리만 입력해서 회원가입을 요청한 경우, `AUTH_PASSWORD_VALIDATORS`에서 막을 수 있다.
  - 사용자가 이메일 또는 ID와 비슷하게 비밀번호를 입력할 경우 막을 수 있다.

<br/>

## 7. AUTH_USER_MODEL

- 사용자를 의미하는 모델을 가리킨다.
- 커스터마이징된 `User`모델로 대체 할 때, 사용한다.

