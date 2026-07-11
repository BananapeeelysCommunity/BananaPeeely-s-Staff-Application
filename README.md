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
background:#1a1a1a; /* DARK MODE */
color:white;
overflow-x:hidden;
}

/* Banana gold accents */
.glass{
width:700px;
max-width:92%;
background:rgba(255,215,0,.12);
backdrop-filter:blur(18px);
border-radius:25px;
padding:40px;
box-shadow:0 15px 40px rgba(0,0,0,.45);
text-align:center;
margin:auto;
border:1px solid rgba(255,215,0,.25);
}

h1{
font-size:34px;
margin-bottom:15px;
color:#ffd400;
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
background:#ffea4d;
}

input,textarea,select{
width:100%;
padding:15px;
margin-top:15px;
border:none;
border-radius:12px;
font-size:16px;
background:rgba(255,255,255,.12);
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
color:#ffd400;
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
background:#ffd400;
transition:.1s;
}

#percent{
margin-top:10px;
font-size:22px;
color:#ffd400;
}

.success{
font-size:30px;
font-weight:600;
margin-top:20px;
color:#00ff7f;
}
</style>
</head>

<body>

<!-- LOADING SCREEN -->
<div class="page-center" id="loading" style="display:flex;justify-content:center;align-items:center;min-height:100vh;">
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
<div class="page-center hidden" id="formPage" style="display:flex;justify-content:center;align-items:center;min-height:100vh;">
<div class="glass">
<h1>Staff Application</h1>
<p>Please answer honestly.</p>

<input id="name" placeholder="Name:">
<input id="discordUser" placeholder="Your Discord Username:">
<input id="age" placeholder="Age:">
<input id="activeTime" placeholder="During which time of the day are you usually active?">

<textarea id="experienceLevel" placeholder="What's your level of experience with moderation?"></textarea>
<textarea id="bringStaff" placeholder="What would you add/bring to the staff team?"></textarea>

<!-- SPAM SELECT -->
<select id="spamAction">
<option value="">If someone is spamming a lot, what would you do?</option>
<option value="Mute">Mute</option>
<option value="Warn and Mute">Warn and Mute</option>
<option value="Kick">Kick</option>
<option value="Ban">Ban</option>
</select>

<!-- RACIAL SLURS SELECT -->
<select id="slurAction">
<option value="">If someone is cussing and saying racial slurs, what would you do?</option>
<option value="Mute">Mute</option>
<option value="Warn and Mute">Warn and Mute</option>
<option value="Kick">Kick</option>
<option value="Ban">Ban</option>
</select>

<select id="grammar">
<option value="">Do you know that you must use grammar?</option>
<option value="Yes">Yes</option>
<option value="No">No</option>
</select>

<select id="abuse">
<option value="">Do you know that abusing powers will get you demoted?</option>
<option value="Yes">Yes</option>
<option value="No">No</option>
</select>

<select id="disrespect">
<option value="">Do you know that disrespecting staff will get you demoted?</option>
<option value="Yes">Yes</option>
<option value="No">No</option>
</select>

<textarea id="extra" placeholder="Anything else you'd like to add? (Optional)"></textarea>

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
{ name: "Name", value: document.getElementById("name").value || "None" },
{ name: "Discord Username", value: document.getElementById("discordUser").value || "None" },
{ name: "Age", value: document.getElementById("age").value || "None" },
{ name: "Active Time", value: document.getElementById("activeTime").value || "None" },
{ name: "Moderation Experience", value: document.getElementById("experienceLevel").value || "None" },
{ name: "What They Bring", value: document.getElementById("bringStaff").value || "None" },
{ name: "Spam Action", value: document.getElementById("spamAction").value || "None" },
{ name: "Racial Slur Action", value: document.getElementById("slurAction").value || "None" },
{ name: "Grammar", value: document.getElementById("grammar").value || "None" },
{ name: "Abuse of Powers", value: document.getElementById("abuse").value || "None" },
{ name: "Disrespecting Staff", value: document.getElementById("disrespect").value || "None" },
{ name: "Extra Info", value: document.getElementById("extra").value || "None" }
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
