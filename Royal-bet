<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>NovaBet</title>

<style>

body{
font-family:Arial;
background:#0f172a;
color:white;
text-align:center;
margin:0;
}

header{
background:#020617;
padding:20px;
font-size:28px;
}

nav{
background:#1e293b;
padding:10px;
}

nav button{
margin:5px;
padding:10px 20px;
border:none;
border-radius:5px;
background:#22c55e;
color:white;
cursor:pointer;
}

.container{
margin-top:40px;
}

input{
padding:10px;
margin:5px;
border-radius:5px;
border:none;
}

.hidden{
display:none;
}

.card{
background:#1e293b;
padding:20px;
margin:10px;
border-radius:10px;
display:inline-block;
}

</style>
</head>

<body>

<header>NovaBet 🎰</header>

<nav>
<button onclick="show('home')">Home</button>
<button onclick="show('login')">Login</button>
<button onclick="show('register')">Register</button>
</nav>

<div id="home" class="container">
<h1>Welcome to NovaBet</h1>
<p>Sports Betting & Casino Demo</p>
</div>

<div id="register" class="container hidden">
<h2>Register</h2>
<input id="regUser" placeholder="Username"><br>
<input id="regPass" type="password" placeholder="Password"><br>
<button onclick="register()">Create</button>
<p id="regMsg"></p>
</div>

<div id="login" class="container hidden">
<h2>Login</h2>
<input id="logUser" placeholder="Username"><br>
<input id="logPass" type="password" placeholder="Password"><br>
<button onclick="login()">Login</button>
<p id="logMsg"></p>
</div>

<div id="dashboard" class="container hidden">
<h2>User Dashboard</h2>
<p id="userName"></p>
<p>Balance: <span id="balance"></span> €</p>

<button onclick="bet()">Bet 5€</button>
<button onclick="logout()">Logout</button>
</div>

<div id="admin" class="container hidden">

<h2>Admin Panel</h2>

<input id="targetUser" placeholder="Username"><br>
<input id="amount" placeholder="Credits"><br>

<button onclick="addCredit()">Add Credits</button>
<button onclick="removeCredit()">Remove Credits</button>

<p id="adminMsg"></p>

</div>

<script>

if(!localStorage.getItem("admin")){

localStorage.setItem("admin",JSON.stringify({
password:"1234"
}))

}

function show(page){

let pages=["home","login","register","dashboard","admin"]

pages.forEach(p=>{
document.getElementById(p).classList.add("hidden")
})

document.getElementById(page).classList.remove("hidden")

}

function register(){

let user=document.getElementById("regUser").value
let pass=document.getElementById("regPass").value

if(!user||!pass)return

let data={
password:pass,
balance:20
}

localStorage.setItem(user,JSON.stringify(data))

document.getElementById("regMsg").innerText="Account created"

}

function login(){

let user=document.getElementById("logUser").value
let pass=document.getElementById("logPass").value

if(user==="admin"){

let admin=JSON.parse(localStorage.getItem("admin"))

if(pass===admin.password){

show("admin")
return

}

}

let data=JSON.parse(localStorage.getItem(user))

if(!data || data.password!==pass){

document.getElementById("logMsg").innerText="Wrong login"

return

}

localStorage.setItem("currentUser",user)

loadDashboard()

show("dashboard")

}

function loadDashboard(){

let user=localStorage.getItem("currentUser")

let data=JSON.parse(localStorage.getItem(user))

document.getElementById("userName").innerText="User: "+user

document.getElementById("balance").innerText=data.balance

}

function bet(){

let user=localStorage.getItem("currentUser")

let data=JSON.parse(localStorage.getItem(user))

if(data.balance<5){

alert("No balance")

return

}

data.balance-=5

localStorage.setItem(user,JSON.stringify(data))

loadDashboard()

}

function logout(){

localStorage.removeItem("currentUser")

show("home")

}

function addCredit(){

let user=document.getElementById("targetUser").value
let amount=parseInt(document.getElementById("amount").value)

let data=JSON.parse(localStorage.getItem(user))

if(!data){

document.getElementById("adminMsg").innerText="User not found"
return

}

data.balance+=amount

localStorage.setItem(user,JSON.stringify(data))

document.getElementById("adminMsg").innerText="Credits added"

}

function removeCredit(){

let user=document.getElementById("targetUser").value
let amount=parseInt(document.getElementById("amount").value)

let data=JSON.parse(localStorage.getItem(user))

if(!data){

document.getElementById("adminMsg").innerText="User not found"
return

}

data.balance-=amount

localStorage.setItem(user,JSON.stringify(data))

document.getElementById("adminMsg").innerText="Credits removed"

}

</script>

</body>
</html>
