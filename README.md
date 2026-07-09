





<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Bananapeeely Staff Application</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Poppins,sans-serif;
}

body{
background:linear-gradient(-45deg,#ffcb05,#ffd94d,#ffea87,#ffe38b);
background-size:400% 400%;
animation:bg 12s ease infinite;
color:white;
overflow-x:hidden;
}

@keyframes bg{
0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}
}

.page-center{
display:flex;
justify-content:center;
align-items:center;
min-height:100vh;
padding:40px 0;
}

.glass{
width:700px;
max-width:92%;
background:rgba(255,255,255,.15);
backdrop-filter:blur(18px);
border-radius:25px;
padding:40px;
box-shadow:0 15px 40px rgba(0,0,0,.25);
text-align:center;
margin:auto;
}

h1{
font-size:34px;
margin-bottom:15px;
}

p{
opacity:.9;
}

button{
margin-top:20px;
padding:14px 35px;
border:none;
border-radius:14px;
background:#ffd400;
font-size:18px;
font-weight:600;
cursor:pointer;
transition:.3s;
}

button:hover{
transform:scale(1.05);
background:#fff176;
}

input,textarea{
width:100%;
padding:15px;
margin-top:15px;
border:none;
border-radius:12px;
font-size:16px;
background:rgba(255,255,255,.2);
color:white;
outline:none;
}

textarea{
resize:none;
height:120px;
}

::placeholder{
color:white;
opacity:.8;
}

.hidden{
display:none;
}

#banana{
font-size:120px;
animation:bounce 1s infinite;
}

@keyframes bounce{
50%{transform:translateY(-15px);}
}

.progress{
width:100%;
height:18px;
background:rgba(255,255,255,.2);
border-radius:50px;
margin-top:30px;
overflow:hidden;
}

.bar{
height:100%;
width:0%;
background:white;
transition:.1s;
}

#percent{
margin-top:10px;
font-size:22px;
}

.success{
font-size:30px;
font-weight:600;
margin-top:20px;
}
</style>
</head>

<body>

<!-- LOADING SCREEN -->
<div class="page-center" id="loading">
<div class="glass">
<div id="banana">🍌</div>
<h1>Bananapeeely's Community</h1>

<div class="progress">
<div class="bar" id="bar"></div>
</div>

<div id="percent">0%</div>
</div>
</div>

<!-- APPLICATION FORM -->
<div class="page-center hidden" id="formPage">
<div class="glass">
<h1>Staff Application</h1>
<p>Please answer honestly.</p>

<input id="discordUser" placeholder="Discord Username:">
<input id="discordID" placeholder="Discord ID:">
<input id="robloxUser" placeholder="Roblox Username:">
<input id="robloxID" placeholder="Roblox ID:">

<textarea id="whyStaff" placeholder="Why do you wish to be staff?"></textarea>
<textarea id="positiveImpact" placeholder="How will you positively affect the community?"></textarea>
<textarea id="experience" placeholder="Do you have any past experience?"></textarea>

<button onclick="submitForm()">Submit Application</button>

<div id="result" class="success hidden">Application Submitted!</div>
</div>
</div>

<script>
// Loading animation
let bar = document.getElementById("bar");
let percent = document.getElementById("percent");
let load = 0;

let loadingInterval = setInterval(() => {
load++;
bar.style.width = load + "%";
percent.innerText = load + "%";

if(load >= 100){
clearInterval(loadingInterval);
document.getElementById("loading").classList.add("hidden");
document.getElementById("formPage").classList.remove("hidden");
window.scrollTo(0,0);
}
}, 30);

// Webhook submission
function submitForm(){
const webhook = "https://discord.com/api/webhooks/1524703860973637652/xpD4RkkMSYLCEdBGflFnoZ4fAr9mDX_Rcf8n_6bvC88IW0gjG6QJ9Am-uAuIaHpoNizX";

const payload = {
content: "**New Staff Application Submitted**",
embeds: [{
title: "Bananapeeely Staff Application",
color: 16763904,
fields: [
{ name: "Discord User", value: document.getElementById("discordUser").value || "None" },
{ name: "Discord ID", value: document.getElementById("discordID").value || "None" },
{ name: "Roblox User", value: document.getElementById("robloxUser").value || "None" },
{ name: "Roblox ID", value: document.getElementById("robloxID").value || "None" },
{ name: "Why Staff?", value: document.getElementById("whyStaff").value || "None" },
{ name: "Positive Impact", value: document.getElementById("positiveImpact").value || "None" },
{ name: "Experience", value: document.getElementById("experience").value || "None" }
]
}]
};

fetch(webhook, {
method: "POST",
headers: { "Content-Type": "application/json" },
body: JSON.stringify(payload)
});

document.getElementById("result").classList.remove("hidden");
window.scrollTo(0, document.body.scrollHeight);
}
</script>

</body>
</html>
