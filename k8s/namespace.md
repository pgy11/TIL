# Namespace

## 1. Namespace?
* Namespace를 이용하면, 자원 접근이 쉬워진다.

  * 어떤 곳에 위치했는지 알 수 있음
  * Namespace의 중복에 유의

  <br/>

* service명, namespace, service, domain순으로 접근

<br/>

## 2. 예제

- ```
  // kube-system안의 자원에 접근할 때
  kube get pods --namespace=kube-system
  ```

- ```
  // dev라는 namespace에서 pod를 정의할 때
  kubectl create -f pod-definition.yml --namespace=dev
  ```

- ```yaml
  // yaml파일에서 정의하기
  apiVersion: v1
  kind: Pod
  metadata: 
    name: myapp-pod
    namespace: dev
    labels: 
      app: myapp
  
  spec:
    containers:
    - name: nginx-container
      image: nginx
  ```

- ```yaml
  // namespace-dev.yml
  apiVersion: v1
  kind: Namespace
  metadata:
    name: dev
  
  // Namespace 생성하기
  // kubectl create -f namespace-dev.yml
  // kubectl create namespace dev
  ```

<br/>

## 3. Namespace Swtiching

- ```
  // 다른 namespace로 이동하기
  kubectl config set-context $(kubectl config current-context) --namespace=dev
  ```

- ```
  // 다른 namespace에 있는 파드 조회하기
  kubectl get pods --namespace=default
  kubectl get pods --namespace=prod
  ```

- ```
  // 모든 namepsace에 있는 파드 조회하기
  kubectl get pods --all-namespaces
  ```

- 

