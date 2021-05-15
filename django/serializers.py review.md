# Serializers.py review

## 1. Serializer

- **쿼리 셋이나 모델 객체같은 복잡한 데이터를 파이썬에서 제공하는 자료형으로 변환하게 해준다.**(i.e. 파이썬에서 제공하는 자료형으로 바꿔주면 JSON, XML로 쉽게 렌더링 될 수 있음)

- `Seirailizer` class는 또한 **역직렬화 기능**도 제공한다.(i.e. 파싱된 데이터가를 장고 모델로 변환)

- 예제

  - 간단한 class가 아래와 같이 존재한다고 하자.

  ```python
  from datetime import datetime
  
  class Comment:
      def __init__(self, email, content, created=None):
          self.email = email
          self.content = content
          self.created = created or datetime.now()
  
  comment = Comment(email='leila@example.com', content='foo bar')
  ```

  <br/>

  - `Commnet` 객체에 상응하는 데이터를 직렬화/역직렬화하는 `Serializer` class를 아래와 같이 만들 수 있다.

  ```python
  from rest_framework import serializers
  
  class CommentSerializer(serializers.Serializer):
      email = serializers.EmailField()
      content = serializers.CharField(max_length=200)
      created = serializers.DateTimeField()
  ```

  <br/>

- `validate()`

  - 역직렬화를 할 때(파싱된 데이터 -> 장고 모델 객체), `is_valid()`를 반드시 호출해야하는데, `is_valid()`를 호출하면 `validate()`가 호출된다. 다시 말해서, 장고 모델 객체로 만들기 전에, 유효성 검사 로직을 `validate()`에서 작성하면 된다.

  <br/>

- Serializer 객체의 `save()`를 호출 할 때, `create()` 또는 `update()`가 호출된다.

## 2. ModelSerializer

- 정의된 장고모델로 매핑하기위해 serializer class를 사용한다.

- 모델 필드에 상응하는 필드와 함께, `Serializer` class를 자동적으로 생성해 주는 쉬운 방법을 제공한다.

- `ModelSerializer` class는 `Serializer` class의 역할과 비슷하지만 차이점이 존재한다.

  -  모델에 기반한 필드를 자동적으로 생성한다.
  - serialzier에 대한 검증 수단을 제공한다.
  - `create()`, `update()`에 관한 기본 구현를 포함한다.

  <br/>

- 예제

  - `Serializer` class의 경우 필드의 타입을 하나하나 입력해야했다. 하지만 `ModelSerializer`의 경우, `Meta` class에서 제공하는 `fields`를 이용하여, 간단한게 필드명을 입력할 수 있다.

  ```python
  class AccountSerializer(serializers.ModelSerializer):
      class Meta:
          model = Account
          fields = ['id', 'account_name', 'users', 'created']
  ```

  <br/>

## 3.  HyperlinkedModelSerializer

- `ModelSerializer` class와 비슷한 역할을 하지만, 관계를 표현하기 위해, 하이퍼링크를 사용한다는 점에서 다르다.(FDS프로젝트에서 `HyperlinkedModelSerializer` class 대신 `ModelSerializer` class를 사용할 수 있었다..)

<br/>

## 4. UniqueValidator

- 필드의 유일성을 검사하는 class이다.

- 회원가입을 할 때 ID 중복검사에 사용하면 유용하다.

- `Serializer` class에서 필드명을 작성할 때, 필드의 인수명 `validators`에 할당하면 된다.

- 예시

  ```python
  class MemberCreateSerializer(serializers.Serializer):
      userid = serializers.CharField(required=True, validators=[
          UniqueValidator(queryset=Member.objects.all())
      ])
      email = serializers.EmailField(required=True, validators=[
          UniqueValidator(queryset=Member.objects.all())
      ])
  ```

  <br/>

  