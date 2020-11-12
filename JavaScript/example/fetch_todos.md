# todos 

## fetch 이용한 todos

```javascript
// State
let todos = [];
let state = "all";

// DOMS
const $todos = document.querySelector(".todos");
const $inputTodo = document.querySelector(".input-todo");
const $completeAll = document.querySelector(".complete-all");
const $clearCompleted = document.querySelector(".clear-completed");
const $completedTodos = document.querySelector(".completed-todos");
const $activeTodos = document.querySelector(".active-todos");
const $nav = document.querySelector(".nav");
const $all = document.getElementById("all");
const $active = document.getElementById("active");
const $completed = document.getElementById("completed");

// 함수 정의
const fetchTodos = () => {
  fetch("/todos")
    .then((res) => res.json())
    .then((_todos) => {
      todos = _todos;
    })
    .then(render)
    .catch(console.error());
};

const render = () => {
  $todos.innerHTML = todos
    .filter((todo) =>
      state === "active"
        ? !todo.completed
        : state === "complete"
        ? todo.completed
        : todo
    )
    .map(({ id, content, completed }) => {
      return `<li id="${id}" class="todo-item">
        <input id="ck-my${id}" class="checkbox" type="checkbox" ${
        completed ? "checked" : ""
      }>
        <label for="ck-my${id}">${content}</label>
        <i class="remove-todo far fa-times-circle"></i>
      </li>`;
    })
    .join("");
  $activeTodos.textContent = countActive();
  $completedTodos.textContent = countClear();
};

const getNextId = () => {
  return todos.length ? Math.max(...todos.map((todo) => todo.id)) + 1 : 1;
};

const addTodo = (content) => {
  todos = [{ id: getNextId(), content, completed: false }, ...todos];
  render();
  console.log(todos);
};

const removeTodo = (id) => {
  todos = todos.filter((todo) => todo.id !== +id);
  render();
};

const reset = () => {
  $inputTodo.value = "";
  $inputTodo.focus();
};

const countClear = () => {
  return todos.filter((todo) => todo.completed).length;
};

const countActive = () => {
  return todos.filter((todo) => !todo.completed).length;
};

window.onload = fetchTodos();

// 이벤트
$inputTodo.onkeyup = (e) => {
  if (e.key !== "Enter" || !$inputTodo.value) return;
  fetch("/todos", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      id: getNextId(),
      content: `${$inputTodo.value}`,
      completed: false,
    })
      .then((res) => res.json())
      .then((_todos) => {
        todos = _todos;
      })
      .then(render)
      .catch(console.error()),
  });
};

$todos.onclick = (e) => {
  if (!e.target.matches(".remove-todo")) return;
  const { id } = e.target.parentNode;
  fetch(`todos/${id}`, { method: "DELETE" })
    .then((res) => res.json())
    .then((_todos) => {
      todos = _todos.map((todo) => todo);
    })
    .then(render)
    .catch(console.error);
};

$todos.onchange = ({ target }) => {
  const id = target.parentNode.id;
  fetch(`/todos/${id}`, {
    method: "PATCH",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ completed: target.checked }),
  })
    .then((res) => res.json())
    .then((_todos) => (todos = _todos))
    .then(render)
    .catch(console.error());

  $completedTodos.textContent = countClear();
  $activeTodos.textContent = countActive();
};

$completeAll.onchange = (e) => {
  fetch("/todos/completed", {
    method: "PATCH",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ completed: checked }),
  })
    .then((res) => res.json())
    .then((_todos) => {
      todos = _todos;
    })
    .then(render)
    .catch(console.error());
};

$clearCompleted.onclick = (e) => {
  fetch("todos/completed", { method: "DELETE" })
    .then((res) => res.json())
    .then((_todos) => {
      todos = _todos.map((todo) => todo);
    })
    .then(render)
    .catch(console.error);
  document.getElementById("ck-complete-all").checked = false;
  $completedTodos.textContent = countClear();
  $activeTodos.textContent = countActive();
  render();
};

$nav.onclick = (e) => {
  [...$nav.children].forEach(($li) => $li.classList.remove("active"));
  e.target.classList.add("active");
};

$all.onclick = (e) => {
  state = "all";
  render();
};

$active.onclick = (e) => {
  state = "active";
  render();
};

$completed.onclick = (e) => {
  state = "complete";
  render();
};

```

