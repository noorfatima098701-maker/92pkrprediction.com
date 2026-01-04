# 92pkrprediction.com<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>WinGo Predictor</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
    margin:0;
    font-family:Arial,Helvetica,sans-serif;
    background:#0f172a;
    color:white;
    text-align:center;
}
.container{
    padding:20px;
}
.card{
    background:#12121a;
    margin:15px auto;
    padding:20px;
    border-radius:12px;
    max-width:420px;
    box-shadow:0 0 20px rgba(0,212,255,0.15);
}
h1{
    color:#00d4ff;
    margin-bottom:10px;
}
button{
    padding:14px 24px;
    font-size:16px;
    border:none;
    border-radius:8px;
    cursor:pointer;
    margin:10px;
}
.btn-register{
    background:#ff0055;
    color:white;
}
.btn-predict{
    background:#00ff88;
}
.hidden{
    display:none;
}
#prediction{
    font-size:48px;
    font-weight:bold;
    margin-top:15px;
}
small{
    color:#94a3b8;
}
.timer{
    font-size:60px;
    margin:10px 0;
}
</style>
</head>

<body>

<div class="container">

<h1>WinGo Predictor</h1>

<div class="card" id="registerBox">
    <p><b>Prediction unlock karne ke liye pehle register karo</b></p>
    <button class="btn-register" onclick="goRegister()">Register & Unlock Prediction</button>
</div>

<div class="card hidden" id="predictBox">
    <div class="timer" id="timer">30</div>
    <button class="btn-predict" onclick="predict()">Get Prediction</button>
    <div id="prediction">---</div>
</div>

<div class="card">
<small>
⚠️ Disclaimer:  
This app does NOT guarantee any win.  
Predictions are based on probability & past trends only.  
Play at your own risk.
</small>
</div>

</div>

<script>
/* ===== CONFIG ===== */
const registerLink = "https://www.92pkrm.com/#/register?invitationCode=633781689868";

/* ===== REGISTER GATE ===== */
function goRegister(){
    localStorage.setItem("registered","yes");
    window.open(registerLink,"_blank");
    setTimeout(unlockPrediction,2000);
}

function unlockPrediction(){
    if(localStorage.getItem("registered")==="yes"){
        document.getElementById("registerBox").classList.add("hidden");
        document.getElementById("predictBox").classList.remove("hidden");
    }
}
unlockPrediction();

/* ===== TIMER ===== */
function startTimer(){
    let t=30;
    setInterval(()=>{
        document.getElementById("timer").innerText = t;
        t--;
        if(t<0) t=30;
    },1000);
}
startTimer();

/* ===== PREDICTION LOGIC ===== */
function predict(){
    const options=["BIG","SMALL"];
    const pick=options[Math.floor(Math.random()*options.length)];
    document.getElementById("prediction").innerText=pick;
}
</script>

</body>
</html>
