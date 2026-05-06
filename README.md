# finanza-<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fin Dashboard Pro</title>

<style>
body {
font-family: Arial;
background: #0b1220;
color: white;
margin: 0;
padding: 20px;
}

.card {
background: #1e293b;
padding: 15px;
margin: 10px 0;
border-radius: 12px;
}

input, select {
padding: 8px;
margin: 5px;
border-radius: 6px;
border: none;
}

button {
padding: 10px;
border-radius: 8px;
border: none;
cursor: pointer;
background: #3b82f6;
color: white;
margin-top: 10px;
}

.result {
font-size: 18px;
margin-top: 10px;
}
</style>
</head>

<body>

<h1>📊 Fin Dashboard Pro (Simulation Engine)</h1>

<div class="card">
<h2>💰 PAC Simulator</h2>

<label>Importo mensile (€)</label><br>
<input id="pac" type="number" value="300"><br>

<label>Anni investimento</label><br>
<input id="years" type="number" value="20"><br>

<button onclick="simulatePAC()">Simula</button>

<div class="result" id="pacResult"></div>
</div>

<div class="card">
<h2>🌍 Portfolio Builder</h2>

<input id="ticker" placeholder="Inserisci ticker (es. AAPL)">
<button onclick="addAsset()">Aggiungi asset</button>

<ul id="portfolio"></ul>
</div>

<div class="card">
<h2>📉 Scenario Macro</h2>

<select id="scenario">
<option value="normal">Crescita normale</option>
<option value="recession">Recessione</option>
<option value="crisis">Crisi finanziaria</option>
<option value="war">Shock geopolitico</option>
<option value="tech">Boom tecnologico</option>
<option value="inflation">Alta inflazione</option>
</select>

<button onclick="runScenario()">Simula scenario</button>

<div class="result" id="scenarioResult"></div>
</div>

<script>

let portfolio = [];

function simulatePAC() {
let monthly = parseFloat(document.getElementById("pac").value);
let years = parseInt(document.getElementById("years").value);

let months = years * 12;

// rendimento medio simulato (non predittivo)
let avgReturn = 0.07;

let total = 0;

for (let i = 0; i < months; i++) {
total = (total + monthly) * (1 + avgReturn / 12);
}

document.getElementById("pacResult").innerHTML =
"📈 Capitale stimato: " + total.toFixed(0) + " €";
}

function addAsset() {
let ticker = document.getElementById("ticker").value.toUpperCase();
if (!ticker) return;

portfolio.push(ticker);

let li = document.createElement("li");
li.innerText = ticker;
document.getElementById("portfolio").appendChild(li);
}

function runScenario() {
let scenario = document.getElementById("scenario").value;

let impact = 1;

if (scenario === "normal") impact = 1;
if (scenario === "recession") impact = 0.7;
if (scenario === "crisis") impact = 0.5;
if (scenario === "war") impact = 0.6;
if (scenario === "tech") impact = 1.3;
if (scenario === "inflation") impact = 0.8;

document.getElementById("scenarioResult").innerHTML =
"📊 Impatto stimato portfolio: x" + impact;
}

</script>

</body>
</html>