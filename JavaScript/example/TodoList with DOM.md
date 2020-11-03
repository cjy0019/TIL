# Todo List 예제



## DOM api를 이용한 Todo List

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
        <li>
          <label><input type="checkbox" /><span>HTML</span></label
          ><button class="remove">X</button>
        </li>
      </ul>
    </div>

    <script>
      // DOMs
      const $todos = document.querySelector(".todos");
      const $inputTodo = document.querySelector(".input-todo");
      const $btnAdd = document.querySelector(".add");

      // 함수 정의 부분
      // 할일 추가하기
      const addTodo = (content) => {
        const $li = document.createElement("li");
        const $label = document.createElement("label");
        const $input = document.createElement("input");
        const $span = document.createElement("span");
        const $button = document.createElement("button");

        $label.appendChild($input);
        $label.appendChild($span);

        $input.setAttribute("type", "checkbox");
        $span.textContent = content;
        $button.textContent = "X";
        $button.classList.add("remove");

        $li.appendChild($label);
        $li.appendChild($button);

        $todos.insertBefore($li, $todos.firstChild);
      };

      // 이벤트 핸들러
      // Enter치면 todo 추가
      $inputTodo.onkeyup = (e) => {
        if (e.key !== "Enter" || !$inputTodo.value) return;
        addTodo($inputTodo.value);
        console.log($todos);
        $inputTodo.value = "";
        $inputTodo.focus();
      };

      // 클릭 이벤트 발생시 todo 추가
      $btnAdd.onclick = (e) => {
        if (!$inputTodo.value) return;
        addTodo($inputTodo.value);
        $inputTodo.value = "";
        $inputTodo.focus();
      };
    </script>
  </body>
</html>

```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/todoimg1.PNG?raw=true" width="70%"></p>