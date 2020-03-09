# 템플릿 문법

뷰로 화면을 조작하는 방법이다. 템플릿 문법은 크게 데이터 바인딩과 디렉티브로 나눌 수 있다.

## 데이터 바인딩

```javascript
<div>{{ something }}</div>

new Vue({
    data: {
        something: '머스타취(콧수염)괄호 사용'
    }
});
```

=> 가장 기본적인 데이터 바인딩 방식. 코드를 실행하면 화면에 머스타취(콧수염)괄호 사용 이 출력 된다.

## 디렉티브

```javascript
<div>
    기생충 <span v-if="show">4관왕</span>
</div>

new Vue({
    data: {
        show: false
    }
});
```

=> show 라는 데이터 속성 값에 따라 출력을 결정할 때 v-if 디렉티브를 사용했다.

```javascript
<ul>
    <li v-for="name in friends">{{ name }}</li>
</ul>

new Vue({
    data: {
        friends: ['kangho', 'jeonghwan', 'seonghan', 'minhyuk', 'munhwa', 'seungmoo']
    }
});
```

=> for 문을 이용한 디렉티브이다.

이 외에도 v-bind, v-on, v-model 등이 많이 사용 된다.
