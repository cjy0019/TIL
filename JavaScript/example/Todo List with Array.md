## Todo List 배열 활용

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
        list-style-type: none;
        padding: 0;
      }
      .todos > li > label > span {
        display: inline-block;
        width: 120px;
        padding: 0 10px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <input type="text" class="input-todo" placeholder="enter todo!" />
      <button class="add">add</button>
      <ul class="todos">
        <!-- <li>
          <label><input type="checkbox" /><span>html</span></label>
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

      // 함수 정의 부분
      // 배열 불러오기
      const fetchTodos = () => {
        return [
          { id: 3, content: "HTML", completed: false },
          { id: 2, content: "CSS", completed: true },
          { id: 1, content: "Javascript", completed: false },
        ];
      };

      // 화면에 렌더링 해주는 함수
      const render = () => {
        let html = "";
        todos
          .map(
            (todo) =>
              (html += `<li id=${todo.id}>
                  <label><input type="checkbox" ${
                    todo.completed ? "checked" : ""
                  } /><span>${todo.content}</span></label>
                  <button class="remove">X</button>
                </li>`)
          )
          .join("");
        $todos.innerHTML = html;
      };

      //할일 추가 함수
      const addTodo = (content) => {
        todos = [{ id: 4, content, completed: false }, ...todos];
        render();
      };

      //리셋 함수
      const reset = () => {
        $inputTodo.value = "";
        $inputTodo.focus();
      };

      // 이벤트 핸들러
      // window가 온로드 되었을 때 배열에 값을 불러온다.
      window.onload = () => {
        todos = fetchTodos();
        render();
      };

      // Enter 했을 때 todo 추가하기
      $inputTodo.onkeyup = (e) => {
        if (e.key !== "Enter" || !$inputTodo.value) return;
        addTodo($inputTodo.value);
        reset();
      };

      // add버튼 눌렀을 때 todo 추가하기
      $btnAdd.onclick = (e) => {
        if (!$inputTodo.value) return;
        addTodo($inputTodo.value);
        reset();
      };
    </script>
  </body>
</html>

```

