//html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Todo List</title>
  </head>
  <body>
    <h1>todos</h1>
    <form id="form">
      <input type="text" class="input" id="input" placeholder="Enter your todo" autocomplete="off">

      <ul class="todos" id="todos"></ul>
    </form>
    <small>Left click to toggle completed. <br> Right click to delete todo</small>

    <script src="script.js"></script>
  </body>
</html>
//js
const form = document.getElementById('form')
const input = document.getElementById('input')
const todosUL = document.getElementById('todos')

const todos = JSON.parse(localStorage.getItem('todos'))

if(todos) {
    todos.forEach(todo => addTodo(todo))
}

form.addEventListener('submit', (e) => {
    e.preventDefault()

    addTodo()
})

function addTodo(todo) {
    let todoText = input.value

    if(todo) {
        todoText = todo.text
    }

    if(todoText) {
        const todoEl = document.createElement('li')
        if(todo && todo.completed) {
            todoEl.classList.add('completed')
        }

        todoEl.innerText = todoText

        todoEl.addEventListener('click', () => {
            todoEl.classList.toggle('completed')
            updateLS()…
//css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background: linear-gradient(135deg, #fbc2eb, #a6c1ee);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.todo-container {
  background: #ffffff;
  width: 320px;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.todo-container h2 {
  text-align: center;
  margin-bottom: 15px;
  color: #333;
}

input {
  width: 70%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 6px;
  outline: none;
}

button {
  padding: 8px 12px;
  margin-left: 5px;
  background: #6c63ff;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #554eea;
}

ul {
  list-style: none;
  margin-top: 15px;
}

li {
  background: #f4f4f4;
  padding: 8px;
  margin-bottom: 8px;
  border-radius: 6px;
  cursor: pointer;
}

li:hover {
  background: #eaeaea;
}

.completed {
  text-decoration: line-through;
  color: gray;
}
