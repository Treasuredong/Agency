# Agency
<!DOCTYPE html>
<html>
<head>
    <title>简易待办事项</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 500px;
            margin: 50px auto;
            padding: 20px;
        }
        #todo-input {
            width: 70%;
            padding: 10px;
            margin-right: 10px;
        }
        button {
            padding: 10px 15px;
            background: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        ul {
            list-style: none;
            padding: 0;
            margin-top: 20px;
        }
        li {
            padding: 10px;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
        }
        .completed {
            text-decoration: line-through;
            color: #888;
        }
        .delete-btn {
            color: red;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h2>简易待办事项</h2>
    <div>
        <input type="text" id="todo-input" placeholder="输入新任务...">
        <button onclick="addTodo()">添加</button>
    </div>
    <ul id="todo-list"></ul>

    <script>
        function addTodo() {
            const input = document.getElementById('todo-input');
            const task = input.value.trim();
            
            if (task) {
                const li = document.createElement('li');
                li.innerHTML = `
                    <span onclick="toggleComplete(this)">${task}</span>
                    <span class="delete-btn" onclick="deleteTodo(this)">✕</span>
                `;
                document.getElementById('todo-list').appendChild(li);
                input.value = '';
            }
        }
        
        function toggleComplete(element) {
            element.classList.toggle('completed');
        }
        
        function deleteTodo(element) {
            element.parentElement.remove();
        }
        
        // 支持回车键添加任务
        document.getElementById('todo-input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') addTodo();
        });
    </script>
</body>
</html>
