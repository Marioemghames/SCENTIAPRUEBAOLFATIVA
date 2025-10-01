<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SCENTIA AI · Experiencia Olfativa Ultra-Premium</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
<style>
/* ------------------------------------- */
/* 1. CSS VARIABLES & BASE STYLES */
/* ------------------------------------- */
:root {
  --color-gold-primary: #7d5e39;
  --color-gold-accent: #b79c6d;
  --color-text-dark: #2c2c2c;
  --color-text-light: #f7f7f7;
  --bg-body: linear-gradient(135deg, #fcfbf8, #f0e6d6);
  --bg-container: #ffffff;
  --bubble-bot: #f5f0e8;
  --bubble-user: #e3d1b7;
}

body {
  font-family: 'Inter', sans-serif;
  margin: 0; padding: 0;
  background: var(--bg-body);
  display: flex; justify-content: center; align-items: center;
  min-height: 100vh;
  color: var(--color-text-dark);
  overflow: hidden;
}

/* ------------------------------------- */
/* 2. LAYOUT & CONTAINER */
/* ------------------------------------- */
.chat-container {
  width: 90%; max-width: 900px;
  background: var(--bg-container);
  border-radius: 30px;
  display: flex; flex-direction: column;
  height: 90vh;
  box-shadow: 0 40px 100px rgba(0, 0, 0, 0.25);
  overflow: hidden;
  position: relative;
}
.bg-overlay {
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background-image: radial-gradient(var(--color-gold-accent) 1px, transparent 1px);
    background-size: 200px 200px;
    opacity: 0.04;
    pointer-events: none;
    z-index: 0;
}
.chat-header {
  background: linear-gradient(90deg, #fff7ea, #e7d8c7);
  padding: 25px 30px;
  text-align: center;
  font-family: 'Playfair Display', serif;
  font-size: 28px; font-weight: 700;
  color: var(--color-gold-primary);
  letter-spacing: 2px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  position: relative;
  z-index: 10;
}

/* ------------------------------------- */
/* 3. CHAT WINDOW & MESSAGES */
/* ------------------------------------- */
.chat-window {
  flex: 1;
  padding: 25px 30px;
  overflow-y: auto;
  background: transparent;
  z-index: 1;
}
.message {
  max-width: 75%;
  padding: 18px 25px;
  margin: 10px 0;
  border-radius: 25px;
  line-height: 1.55;
  word-wrap: break-word;
  opacity: 0;
  transform: translateY(10px);
  animation: message-fade-in 0.6s forwards cubic-bezier(0.1, 0.7, 1.0, 1.0);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}
@keyframes message-fade-in { 
    to { opacity: 1; transform: translateY(0); } 
}
.bot { 
    background: var(--bubble-bot); 
    border-radius: 25px 25px 25px 6px; 
}
.user { 
    background: var(--bubble-user); 
    border-radius: 25px 25px 6px 25px; 
    margin-left: auto;
}

/* ------------------------------------- */
/* 4. INPUT & BUTTONS */
/* ------------------------------------- */
.chat-input {
  display: flex;
  padding: 20px;
  background: var(--bg-container);
  border-top: 1px solid #eee;
  box-shadow: 0 -8px 20px rgba(0, 0, 0, 0.08);
  z-index: 10;
}
.chat-input input {
  flex: 1;
  padding: 16px 20px;
  border-radius: 28px;
  border: 2px solid #ddd;
  font-size: 17px;
  transition: border-color 0.3s, box-shadow 0.3s;
}
.chat-input input:focus {
  outline: none;
  border-color: var(--color-gold-accent);
  box-shadow: 0 0 10px rgba(179, 143, 79, 0.5); 
}
.chat-input button {
  margin-left: 15px;
  background: var(--color-gold-primary);
  border: none;
  color: var(--color-text-light);
  font-weight: 600;
  padding: 16px 30px;
  border-radius: 28px;
  cursor: pointer;
  transition: background 0.3s, transform 0.1s;
  letter-spacing: 0.5px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}
.chat-input button:hover {
  background: var(--color-gold-accent);
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.25);
}

/* ------------------------------------- */
/* 5. PERFUME CARD & NEW COMMERCE STYLES */
/* ------------------------------------- */
.fragrance-card {
  background: var(--bg-container);
  border: 3px solid var(--color-gold-accent);
  padding: 35px;
  border-radius: 25px;
  margin-top: 30px;
  box-shadow: 0 15px 40px rgba(138, 108, 63, 0.25);
  animation: card-pop-in 0.8s forwards;
  position: relative;
}
.fragrance-card h3 { 
    margin: 0 0 10px; 
    color: var(--color-gold-primary); 
    font-size: 26px; 
    font-family: 'Playfair Display', serif;
}
/* Special Code Box */
.code-box {
    text-align: center;
    padding: 15px;
    margin: 25px 0;
    border: 1px dashed #e0d1b5;
    background: #fdfaf6;
    border-radius: 15px;
}
.special-code {
    font-size: 1.5em;
    font-weight: 700;
    color: var(--color-gold-primary);
    letter-spacing: 2px;
    margin-top: 5px;
    font-family: 'Playfair Display', serif;
}

/* Product Options Layout */
.product-options {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    margin-top: 20px;
    padding-bottom: 25px;
    border-bottom: 1px solid #eee;
}
.option-group h4 {
    font-size: 15px;
    color: #888;
    margin-bottom: 10px;
    font-weight: 500;
}
.selector-btn {
    display: inline-block;
    padding: 10px 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-size: 14px;
    margin-right: 8px;
    cursor: pointer;
    transition: all 0.2s;
}
.selector-btn:hover { border-color: var(--color-gold-accent); }
.selector-btn.selected {
    background: var(--color-gold-primary);
    color: var(--color-text-light);
    border-color: var(--color-gold-primary);
    font-weight: 500;
}

/* Color Options */
.color-selection {
    margin: 25px 0;
}
.color-selection h4 {
    font-size: 15px;
    color: #888;
    margin-bottom: 10px;
    font-weight: 500;
}
.color-swatch {
    display: inline-block;
    width: 30px; height: 30px;
    border-radius: 50%;
    margin-right: 12px;
    cursor: pointer;
    border: 2px solid transparent;
    transition: border-color 0.2s;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
.color-swatch.selected {
    border-color: var(--color-gold-primary);
    box-shadow: 0 0 0 3px #f7f3ed;
}

/* Final Buy Button */
.buy-button {
    width: 100%;
    background: var(--color-gold-primary);
    color: var(--color-text-light);
    border: none;
    padding: 18px;
    border-radius: 12px;
    font-size: 18px;
    font-weight: 700;
    cursor: pointer;
    margin-top: 30px;
    box-shadow: 0 8px 20px rgba(125, 94, 57, 0.4);
    transition: background 0.3s, transform 0.1s, box-shadow 0.3s;
}
.buy-button:hover {
    background: var(--color-gold-accent);
    transform: translateY(-2px);
    box-shadow: 0 10px 25px rgba(125, 94, 57, 0.5);
}
</style>
</head>
<body>

<div class="chat-container">
  <div class="bg-overlay"></div>
  <div class="chat-header">SCENTIA AI · Un Viaje Olfativo ✨</div>
  <div id="chat-window" class="chat-window"></div>
  <div class="chat-input">
    <input id="user-input" type="text" placeholder="Escribe tu respuesta...">
    <button id="send-btn">Enviar</button>
  </div>
</div>

<script>
const chatWindow = document.getElementById("chat-window");
const userInput = document.getElementById("user-input");
const sendBtn = document.getElementById("send-btn");

// Using <strong> tags for correct rendering
const questions = [
  "<strong>Paso 1/9: Identidad.</strong> Por favor, indica tu género (Masculino / Femenino / Otro).",
  "<strong>Paso 2/9: Identidad.</strong> Escribe tu nombre.",
  "<strong>Paso 3/9: Identidad.</strong> Escribe tu apellido.",
  "<strong>Paso 4/9: Preferencia.</strong> ¿Qué aromas prefieres? (Cítricos 🍋, Florales 🌸, Amaderados 🌲, Dulces 🍯, Especiados 🌶️)",
  "<strong>Paso 5/9: Performance.</strong> ¿Prefieres fragancias suaves, moderadas o intensas?",
  "<strong>Paso 6/9: Contexto.</strong> ¿En qué ocasión principal usarías tu perfume? (Diario, Noche, Eventos)",
  "<strong>Paso 7/9: Emoción.</strong> ¿Qué emociones deseas transmitir con tu perfume? (Elegancia ✨, Energía ⚡, Misterio 🌑, Romance ❤️)",
  "<strong>Paso 8/9: Narrativa.</strong> Cuéntame una breve historia o característica que te defina personalmente.",
  "<strong>Paso 9/9: Integración.</strong> ¿Deseas que tu perfume combine con otros productos SCENTIA? (Sí/No)"
];

let answers = [];
let currentQuestion = 0;

function addMessage(text, sender="bot"){
  const msg = document.createElement("div");
  msg.className = "message "+sender;
  msg.innerHTML = text; 
  chatWindow.appendChild(msg);
  chatWindow.scrollTop = chatWindow.scrollHeight;
}

function botAskNext(){
  if(currentQuestion < questions.length){
    setTimeout(()=>addMessage(questions[currentQuestion],"bot"),800);
  } else {
    generatePerfumeDemo();
  }
}

// FINAL PERFUME RESULT with commercial options
function generatePerfumeDemo(){
  addMessage("✨ <strong>SCENTIA AI:</strong> Analizando tu <strong>identidad, memoria y autoexpresión</strong> para la creación final...", "bot");

  const perfumeData = {
    nombre_perfume: "Aura Privée: Código NARRATIVA",
    codigo_olfativo: "SCNT-PVT-1903-RCM",
    notas_top: "Bergamota 🍋 (Alta pureza), Pera Nashi 🍐",
    notas_middle: "Jazmín Sambac 🌸, Madera de Cashmere 🪵",
    notas_base: "Sándalo Mysore 🌲, Almizcle Blanco ☁️",
    intensidad: "Moderada (Eau de Parfum)",
    emociones: "Elegancia ✨ y Misterio 🌑",
  };

  const card = document.createElement("div");
  card.className="fragrance-card";
  card.innerHTML = `
    <h3 style="margin-bottom: 5px;">${perfumeData.nombre_perfume}</h3>
    <div style="font-size: 14px; color: #888; font-weight: 500; margin-bottom: 25px;">
        ${perfumeData.emociones} | ${perfumeData.intensidad}
    </div>

    <div class="code-box">
        <p style="margin: 0 0 5px 0; font-size: 14px;"><strong>Usa este código para tu perfume personal:</strong></p>
        <div class="special-code">${perfumeData.codigo_olfativo}</div>
    </div>
    
    <div class="product-options">
        <div class="option-group">
            <h4>Volumen</h4>
            <div class="selector-btn selected">50 ML</div>
            <div class="selector-btn">100 ML</div>
        </div>
        <div class="option-group">
            <h4>Concentración</h4>
            <div class="selector-btn selected">Eau de Parfum (EDP)</div>
            <div class="selector-btn">Elixir (Máxima Fijación)</div>
        </div>
    </div>

    <div class="color-selection">
        <h4>Color de Botella / Embalaje</h4>
        <div class="color-swatches">
            <div class="color-swatch selected" style="background-color: #f7f3ed;" title="Perla Mate"></div>
            <div class="color-swatch" style="background-color: #636166;" title="Gris Ahumado"></div>
            <div class="color-swatch" style="background-color: #aa9578;" title="Oro Rosado"></div>
        </div>
    </div>
    
    <button class="buy-button">Comprar Ahora</button>

    <div style="margin-top: 30px; border-top: 1px solid #eee; padding-top: 20px;">
        <p style="margin-top: 0;">💧 Notas Top: <strong>${perfumeData.notas_top}</strong></p>
        <p>🌸 Notas Corazón: <strong>${perfumeData.notas_middle}</strong></p>
        <p>🌲 Notas Base: <strong>${perfumeData.notas_base}</strong></p>
    </div>
  `;
  setTimeout(() => {
    chatWindow.appendChild(card);
    chatWindow.scrollTop = chatWindow.scrollHeight;
    addMessage("✅ <strong>¡Fórmula Completada!</strong> Tu fragancia personal ha sido generada.", "bot");
  }, 1200);
}

// Events (remain the same)
sendBtn.addEventListener("click",()=>{
  const text = userInput.value.trim();
  if(!text) return;
  addMessage(text,"user");
  answers.push(text);
  userInput.value="";
  currentQuestion++;
  botAskNext();
});

userInput.addEventListener("keypress", e=>{
  if(e.key==="Enter"){ e.preventDefault(); sendBtn.click(); }
});

// Start conversation
addMessage("👋 Hola. Soy <strong>SCENTIA IA</strong>, tu asistente premium. Comencemos tu viaje íntimo de creación de fragancias.", "bot");
botAskNext();
</script>
</body>
</html>
