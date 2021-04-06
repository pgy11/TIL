# Front에서 해야할 일

## 1. install

1. docker install
2. node install
3. yarn install
4. git install

<br/>

## 2. Source code download

- git clone

<br/>

## 3. build

- yarn build

<br/>

## 4. docker nginx server deploy

- default.conf copy
- build/ nginx application dir에 copy
- chown -R nginx:nginx nginx application dir
- nginx reload
- docker container 실행

위의 사항들을 Dockerfile 또는 docker-compose.yaml에 작성

2,3번의 경우 자동화한다(jenkins, circleci등 tool을 이용해서 script 작성)

