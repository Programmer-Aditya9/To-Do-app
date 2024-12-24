<!DOCTYPE html>
<html>
<head>
    <title>To-Do-List</title>
</head>
<body>
    <div class="container">
        <div class="todo-app">
            <h1>To-Do List <img src="images/icon.png"></h1>
            <div class="row">
                <input type="text" id="input-box" placeholder="Add your text">
                <button onclick="addTask()">Add</button>
            </div>
            <ul class="list-container">
            </ul>
        </div>
    </div>
    
    <script>
        const inputBox = document.querySelector("#input-box");
const listContainer = document.querySelector(".list-container");
const body = document.querySelector("body");
const container = document.querySelector(".container");
const ul = document.querySelector("ul");
function addTask(){
    if(inputBox.value === ''){
        alert("You must write something!");
    }
    else{
        let li = document.createElement("li");
        li.innerHTML = inputBox.value;
        ul.append(li);
        let span = document.createElement("span");
        span.innerHTML = "\u00d7";
        li.appendChild(span);
    }
    inputBox.value = "";
    saveData();
}

ul.addEventListener("click", (e) => {
    if(e.target.tagName === "LI"){
        e.target.classList.toggle("checked");
        saveData();
    }
    else if(e.target.tagName === "SPAN"){
        e.target.parentElement.remove();
        saveData();
    }
}, false);

let saveData = () => {
    localStorage.setItem("data", ul.innerHTML);
}

let showData = () => {
    ul.innerHTML = localStorage.getItem("data");
}

showData();
    </script>

    <style>
        *{
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    box-sizing: border-box;
}

.container{
    width: 100%;
    min-height: 100vh;
    background: linear-gradient(135deg, #696EFF, #F8ACFF);
    padding: 10px;
}
.todo-app{
    width: 100%;
    max-width: 540px;
    background: #fff;
    margin: 100px auto 20px;
    padding: 40px 30px 70px;
    border-radius: 10px;
}

.todo-app h1{
    color: #002765;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}

.todo-app h1 img{
    width: 50px;
    margin-left: 10px;
}

.row{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #edeef0;
    border-radius: 30px;
    padding-left: 20px;
    margin-bottom: 25px;
}

input{
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    padding: 10px;
    font-weight: 14px;
}

button{
    border: none;
    outline: none;  
    padding: 16px 50px;
    background: #ff5945;    
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    border-radius: 40px;
}

ul li{
    list-style: none;
    font-size: 17px;
    font-style: bold;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor: pointer;
    position: relative;
}

ul li::before{
    content: '';
    position: absolute;
    height: 28px;
    width: 28px;
    border-radius: 50%;
    background-image: url(images/unchecked.png);
    background-size: cover;
    background-position: center;
    top: 12px;
    left: 8px;
}

ul li.checked{
    color: #555;
    text-decoration: line-through;
}

ul li.checked::before{
    background-image: url(images/checked.png);
}

ul li span{
    position: absolute;
    right: 0;
    top: 5px;
    width: 40px;
    height: 40px;
    font-size: 22px;
    font-style: bold;
    color: #555;
    line-height: 40px;
    text-align: center;
    border-radius: 50%;
}

ul li.checked {
    color: #555;
    text-decoration: line-through;
}

ul li span:hover{
    background: #edeef0;
    color: #000000;
    transition: all 0.5s ease-in-out;
}
    </style>
</body>
</html>
