# 인스턴스 생성
```javascript
new Vue();
```

```javascript
var vm = new Vue();
console.log(vm);
```
=> 인스턴스의 속성과 메서드 들이 콘솔로 출력.

## Vue 인스턴스의 속성과 API
```javascript
new Vue({
    el: ,
    template: ,
    data: ,
    methods: ,
    created: ,
    watch: ,
});
```
- el : 인스턴스가 그려지는 화면의 시작점
- template : 화면에 표시할 요소
- data : 뷰의 reactivity 가 반영된 데이터 속성
- methods : 화면의 동작과 이벤트 로직을 제어하는 메서드
- created : 뷰의 라이프 사이클과 관련된 속성
- watch : data 에서 정의한 속성이 변화했을 때 추가 동작을 수행할 수 있게 정의하는 속성

## 인스턴스 라이프 사이클

뷰의 인스턴스가 생성되어 소멸되기까지 거치는 과정이 라이프 사이클이다.
인스턴스가 생성되면 내부적으로 다음과 같은 과정이 진행 된다.
- data 속성의 초기화 및 관찰(reactivity 주입)
- 뷰 템플릿 코드 컴파일 (가상DOM -> DOM 변환)
- 인스턴스를 DOM(화면) 에 부착

인스턴스를 화면에 부착한 뒤에 인스턴스의 데이터 변경이 있으면 화면을 재 랜더링 하고 데이터를 갱신하며 (인스턴스 내용 갱신)
컴포넌트,인스턴스,디렉티브 등을 모두 해제 한 뒤에는 인스턴스는 소멸 된다 (인스턴스 소멸)

즉, new Vue() 를 하면 인스턴스 생성 -> 인스턴스 화면 부착 -> 인스턴스 내용 갱신 -> 인스턴스 소멸 의 과정을 거친다.

#라이프 사이클 훅

인스턴스의 특정 시점에 원하는 로직을 구현하기 위해서는 라이프 사이클 훅을 이용해야 한다.
ex) 컴포넌트가 생성되자마자 데이터를 서버에서 받아오고 싶을 때는 created or beforeMount 라이프 사이클 훅을 사용해야 한다.

https://vuejs.org/v2/api/#Options-Lifecycle-Hooks

