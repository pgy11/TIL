# Model.py review

## 1. is_staff

- 관리자 사이트에 접근할 수 있는지 확인하기 위한 변수

<br/>

## 2. is_active

사용자 계정 활성화 여부, `False`로 설정하는 것을 권장함

<br/>

## 3. date_joined

사용자가 서비스에 회원가입을 한 날짜

<br/>

## 4. BaseUserManager

- 기존에 제공되는 `User`모델을 커스터마이징을 할 경우, 모델을 관리하는 `Manager`또한 커스터마이징을 해야한다. 이 때, `BaseUserManager`를 상속해서 커스터마이징을 한다.

- `create_user(username_field, password=None, **other_fields)`

  - 사용자가 정의한 필드를 인수로 주되, 사용자명 필드, 비밀번호는 인수를 따로 준다. 나머지는 `**oter_fields`에 간다.(i.e. 따로 필드를 작성하지 않아도 된다.)

  <br/>

- `create_superuser(username_field, password=None, **other_fields)`

  - 하는 일은 `create_user()`와 동일하지만, 사용자의 권한에서 차이가 있다.(super user가 일반 사용자보다 권한이 많다.)

<br/>

## 5. AbstractBaseUser

- 기존에 제공되는 사용자 모델을 커스터마이징 할 때, `AbstractBaseUser`를 상속하면 쉽게 커스터마이징 할 수 있다.

- `AbstractBaseUser`은 사용자 모델의 핵심 구현체를 제공한다.(e.g. 해시가 적용된 비밀번호, 토큰화된 비밀번호 리셋등)

- 사용을 할 때, 개발자는 핵심 구현체를 자세하게 제공해야한다.

- `USERNAME_FIELD`

  - 유일한 식별자로 사용되는 필드를 `USERNAME_FIELD`에 적어야한다.
  - 어떤 필드가 유일한 식별자면, username필드가 아니더라도 `USERNAME_FIELD`에 적을 수 있다.

  <br/>

- `EMAIL_FIELD`

- `REQUIRED_FIELDS`

  - `createsuperuser` 관리 명령어를 통해 사용자를 생성할 때, 사용된다.
  - 필드가 `blank=True`이거나, 정의되지 않을 때 사용한다.
  - 사용자가 상호적으로 생성하여 추가적인 필드를 포함할 때 사용한다.
  - `USERNAME_FIELD`에 적힌 필드와 비밀번호를 제외한 나머지 필드를 넣어야한다.