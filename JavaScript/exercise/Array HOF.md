# Array HOF 연습 문제

## 1. html 생성

아래 배열을 사용하여 html을 생성하는 함수를 작성하라.

```javascript
const todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function render() {
  let html = '';

  todos.forEach(todo => {

  });

  return html;
}

console.log(render());
/*
<li id="3">
  <label><input type="checkbox">HTML</label>
</li>
<li id="2">
  <label><input type="checkbox" checked>CSS</label>
</li>
<li id="1">
  <label><input type="checkbox">Javascript</label>
</li>
*/
```

**Answer**

```javascript
const todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function render() {
  let html = '';

  todos.forEach(({ id, content, completed }) => {
    html += `<li id="${id}">
    <label><input type="checkbox" ${
      completed ? 'checked' : ''
    }>${content}</label>
  </li>`;
  });

  return html;
}

console.log(render());

/*
<li id="3">
  <label><input type="checkbox">HTML</label>
</li>
<li id="2">
  <label><input type="checkbox" checked>CSS</label>
</li>
<li id="1">
  <label><input type="checkbox">Javascript</label>
</li>
*/
```



## 2. 특정 프로퍼티 값 추출

요소의 프로퍼티(id, content, completed)를 문자열 인수로 전달하면 todos의 각 요소 중, 해당 프로퍼티의 값만을 추출한 배열을 반환하는 함수를 작성하라.

단, for 문이나 Array#forEach는 사용하지 않도록 하자.

```javascript
const todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function getValues(key) {

}

console.log(getValues('id')); // [3, 2, 1]
console.log(getValues('content')); // ['HTML', 'CSS', 'Javascript']
console.log(getValues('completed')); // [false, true, false]
```

**Answer**

```javascript
const todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function getValues(key) {
  return todos.map((todo) => todo[key]);
}

console.log(getValues("id")); // [3, 2, 1]
console.log(getValues("content")); // ['HTML', 'CSS', 'Javascript']
console.log(getValues("completed")); // [false, true, false]
```



## 3. 프로퍼티 정렬

요소의 프로퍼티(id, content, completed)를 문자열 인수로 전달하면 todos의 요소를 정렬하는 함수를 작성하라.

단, todos는 변경되지 않도록 하자.

```javascript
const todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function sortBy(key) {

}

console.log(sortBy('id'));
/*
[
  { id: 1, content: 'Javascript', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 3, content: 'HTML', completed: false }
]
*/
console.log(sortBy('content'));
/*
[
  { id: 2, content: 'CSS', completed: true },
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
console.log(sortBy('completed'));
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false },
  { id: 2, content: 'CSS', completed: true }
]
*/
```

**Answer**

```javascript
const todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function sortBy(key) {
  let todo = todos.sort((a, b) =>
    a[key] > b[key] ? 1 : a[key] < b[key] ? -1 : 0
  );
  return todo;
}

console.log(sortBy("id"));
/*
[
  { id: 1, content: 'Javascript', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 3, content: 'HTML', completed: false }
]
*/
console.log(sortBy("content"));
/*
[
  { id: 2, content: 'CSS', completed: true },
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
console.log(sortBy("completed"));
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false },
  { id: 2, content: 'CSS', completed: true }
]
*/
```



## 4. 새로운 요소 추가

새로운 요소(예를 들어 `{ id: 4, content: 'Test', completed: false }`)를 인수로 전달하면 todos의 선두에 새로운 요소를 추가하는 함수를 작성하라. 단, Array#push는 사용하지 않도록 하자.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function addTodo(newTodo) {

}

addTodo({ id: 4, content: 'Test', completed: false });

console.log(todos);
/*
[
  { id: 4, content: 'Test', completed: false },
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function addTodo(newTodo) {
  return todos.splice(0, 0, newTodo);
}

function addTodo(newTodo) {
  todos = [newTodo, ...todos];
  return todos;
}

addTodo({ id: 4, content: "Test", completed: false });

console.log(todos);
/*
[
  { id: 4, content: 'Test', completed: false },
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
]
*/

```



## 5. 특정 요소 삭제

todos에서 삭제할 요소의 id를 인수로 전달하면 해당 요소를 삭제하는 함수를 작성하라.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function removeTodo(id) {

}

removeTodo(2);

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function removeTodo(id) {
  todos = todos.filter((todo) => todo.id !== id);
}

removeTodo(2);

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```



## 6. 특정 요소의 프로퍼티 값 반전

todos에서 대상 요소의 id를 인수로 전달하면 해당 요소의 completed 프로퍼티 값을 반전하는 함수를 작성하라.

hint) 기존 객체의 특정 프로퍼티를 변경/추가하여 새로운 객체를 생성하려면 `Object.assign`또는 스프레드 문법을 사용한다.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function toggleCompletedById(id) {

}

toggleCompletedById(2);

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

// ES6 스프레드
function toggleCompletedById(id) {
  todos = todos.map((todo) =>
    todo.id === id ? { ...todo, completed: !todo.completed } : todo
  );
}

// Object.assign()
function toggleCompletedById(id) {
  todos = todos.map((todo) =>
    todo.id === id
      ? Object.assign({}, todo, { completed: !todo.completed })
      : todo,
  );
}

toggleCompletedById(2);

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```



##  7. 모든 요소의 completed 프로퍼티 값을 true로 설정

todos의 모든 요소의 completed 프로퍼티 값을 true로 설정하는 함수를 작성하라.

hint) 기존 객체의 특정 프로퍼티를 변경/추가하여 새로운 객체를 생성하려면 `Object.assign` 또는 스프레드 문법을 사용한다.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function toggleCompletedAll() {

}

toggleCompletedAll();

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: true },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: true }
]
*/
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function toggleCompletedAll() {
  todos = todos.map((todo) =>
    todo.completed === false ? { ...todo, completed: !todo.completed } : todo
  );
}

// Object.assign
function toggleCompletedAll() {
  todos = todos.map((todo) => Object.assign({}, todo, { completed: true }));
}

toggleCompletedAll();

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: true },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: true }
]
*/
```



## 8. completed 프로퍼티의 값이 true인요소의 갯수 구하기

todos에서 완료(completed: true)한 할일의 갯수를 구하는 함수를 작성하라.

단, for 문, Array#forEach는 사용하지 않도록 하자.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function countCompletedTodos() {

}

console.log(countCompletedTodos()); // 1
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function countCompletedTodos() {
  return todos.filter((todo) => todo.completed === true).length;
}

console.log(countCompletedTodos()); // 1

```



##  9. id 프로퍼티의 값 중에서 최대값 구하기

todos의 id 프로퍼티의 값 중에서 최대값을 구하는 함수를 작성하라.

단, for 문, Array#forEach는 사용하지 않도록 하자.

```javascript
let todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

function getMaxId() {

}

console.log(getMaxId()); // 3
```

**Answer**

```javascript
let todos = [
  { id: 3, content: "HTML", completed: false },
  { id: 2, content: "CSS", completed: true },
  { id: 1, content: "Javascript", completed: false },
];

function getMaxId() {
  return Math.max(...todos.map((todo) => todo.id));
}
console.log(getMaxId()); // 3
```

