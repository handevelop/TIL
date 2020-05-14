# 일반적인 콜백함수를 사용한 ajax 통신

```javascript

function getData(callbackFunc) {
  $.get('url 주소/products/1', function(response) {
    callbackFunc(response); // 서버에서 받은 데이터 response를 callbackFunc() 함수에 넘겨줌
  });
}

getData(function(tableData) {
  console.log(tableData); // $.get()의 response 값이 tableData에 전달됨
});

```

# promise를 사용한 ajax 통신

```javascript

function getData(callback) {
  // new Promise() 추가
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(response) {
      // 데이터를 받으면 resolve() 호출
      resolve(response);
    });
  });
}

// getData()의 실행이 끝나면 호출되는 then()
getData().then(function(tableData) {
  // resolve()의 결과 값이 여기로 전달됨
  console.log(tableData); // $.get()의 reponse 값이 tableData에 전달됨
});

```

# promise의 3가지 states

Pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
Fulfilled(이행) : 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
Rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태

## Pending(대기)

new Promise() 메서드를 호출하면 대기 상태가 된다.
이 때, 콜백 함수를 선언할 수 있고 콜백 함수의 인자는 resolve, reject 이다.
```javascript
new Promise(function(resolve, reject) {
  // ...
});
```

## Fulfilled(이행)

아래와 같이 콜백함수의 resolve 인자를 실행하면 이행 상태가 된다.
그리고 이행 상태가 되면 then() 을 통해 처리 결과 값을 받아 출력, 처리 등을 할 수 있다.
```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolvedData로 받음
getData().then(function(resolvedData) {
  console.log(resolvedData); // 100
});
```

## Rejected(실패)

아래와 같이 콜백함수의 reject 인자를 실행하면 실패 상태가 된다.
그리고 실패 상태가 되면 실패한 이유를 catch() 로 받을 수 있다.
```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err) {
  console.log(err); // Error: Request is failed
});
```

# 예제

```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(response) {
      if (response) {
        resolve(response);
      }
      reject(new Error("Request is failed"));
    });
  });
}

// 위 $.get() 호출 결과에 따라 'response' 또는 'Error' 출력
getData().then(function(data) {
  console.log(data); // response 값 출력
}).catch(function(err) {
  console.error(err); // Error 출력
});
```