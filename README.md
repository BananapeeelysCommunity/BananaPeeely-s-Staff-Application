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
background:#111; /* DARK MODE */
color:white;
overflow-x:hidden;
overflow-y:auto; /* ALWAYS SCROLLABLE */
}

.glass{
width:700px;
max-width:92%;
background:rgba(255,215,0,.12);
backdrop-filter:blur(18px);
border-radius:25px;
padding:40px;
box-shadow:0 15px 40px rgba(0,0,0,.45);
text-align:center;
margin:40px auto;
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
color:black;
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
background:white; /* WHITE BACKGROUND */
color:black; /* BLACK TEXT */
outline:none;
}

textarea{
resize:none;
height:120px;
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

<div class="glass">
<h1>Staff Application</h1>
<p>Please answer honestly.</p>

<input id="name" placeholder="Name:">
<input id="discordUser" placeholder="Your Discord Username:">
<input id="age" placeholder="Age:">
<input id="activeTime" placeholder="During which time of the day are you usually active?">

<textarea id="experienceLevel" placeholder="What's your level of experience with moderation?"></textarea>
<textarea id="bringStaff" placeholder="What would you add/bring to the staff team?"></textarea>

<select id="spamAction">
<option value="">If someone is spamming a lot, what would you do?</option>
<option value="Mute">Mute</option>
<option value="Warn and Mute">Warn and Mute</option>
<option value="Kick">Kick</option>
<option value="Ban">Ban</option>
</select>

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

<div id="result" class="success" style="display:none;">Application Submitted!</div>
</div>

<script>
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

document.getElementById("result").style.display = "block";
window.scrollTo(0, document.body.scrollHeight);
}
</script>

</body>
</html>
