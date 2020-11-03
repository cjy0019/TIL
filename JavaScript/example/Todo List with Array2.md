## Todo List

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .container {
        width: 300px;
        margin: 30px auto;
      }
      .todos {
        list-style: none;
        padding: 0;
      }
      .todos > li > label > span {
        display: inline-block;
        width: 120px;
        padding: 0 10px;
      }
      .todos > li.compelete span {
        text-decoration: line-through;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <form>
        <input type="text" class="input-todo" placeholder="enter todo!" />
        <button class="add">add</button>
      </form>
      <ul class="todos">
        <!-- <li id="">
          <label><input type="checkbox" /><span>HTML</span></label>
          <button class="remove">X</button>
        </li> -->
      </ul>
    </div>

    <script>
      let todos = [];

      // DOMs
      const $todos = document.querySelector(".todos");
      const $inputTodo = document.querySelector(".input-todo");
      const $btnAdd = document.querySelector(".add");
      const $form = document.querySelector("form");

      // 함수 정의
      const fetchTodos = () => {
        todos = [
          { id: 1, content: "HTML", completed: false },
          { id: 2, content: "CSS", completed: true },
          { id: 3, content: "Javascript", completed: false },
        ].sort((todo1, todo2) => todo2.id - todo1.id);
      };

      // 렌더링 함수
      const render = () => {
        let html = "";
        todos.forEach(({ id, content, completed }) => {
          html += `<li id="${id}">
              <label>
                <input type="checkbox" ${completed ? "checked" : ""} />
                <span>${content}</span>
              </label>
              <button class="remove">X</button>
            </li>`;
        });
        $todos.innerHTML = html;
      };

      // todo 추가
      const addTodo = (content) => {
        todos = [{ id: generateNextId(), content, completed: false }, ...todos];
        render();
      };

      // id 값 구하기
      const generateNextId = () => {
        return todos.length ? Math.max(...todos.map((todo) => todo.id)) + 1 : 1;
      };

      // reset 함수
      const reset = () => {
        $inputTodo.value = "";
        $inputTodo.focus();
      };

      //삭제 함수
      const removeTodo = (id) => {
        todos = todos.filter((todo) => todo.id !== +id);
        render();
      };

      // 토글
      const toggleTodoCompleted = (id) => {
        todos = todos.map((todo) =>
          todo.id === +id ? { ...todo, completed: !todo.completed } : todo
        );
      };

      // 이벤트 핸들러
      window.onload = () => {
        fetchTodos();
        render();
        console.log(todos);
      };

      // Enter했을 때 todo 추가
      $form.onsubmit = (e) => {
        e.preventDefault();
        if (e.key !== "Enter" || !$inputTodo.value) return;
        addTodo($inputTodo.value);
        reset();
      };

      $btnAdd.onclick = (e) => {
        if (!$inputTodo.value) return;
        addTodo($inputTodo.value);
        render();
        reset();
      };

      // 삭제 버튼 이벤트
      $todos.onclick = (e) => {
        if (!e.target.matches(".todos > li > button.remove")) return;
        removeTodo(e.target.parentNode.id);
      };

      // 체크했을 때
      $todos.onchange = (e) => {
        toggleTodoCompleted(e.target.parentNode.parentNode.id);
        console.log(todos);
      };
    </script>
  </body>
</html>
```

