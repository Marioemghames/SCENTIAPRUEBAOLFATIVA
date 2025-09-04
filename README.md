<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SCENTIA · Test Olfativo</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: linear-gradient(135deg, #f7f7f7, #ececec);
      margin: 0; padding: 0;
      display: flex; justify-content: center; align-items: center;
      min-height: 100vh;
    }
    .chat-container {
      background: #fff;
      max-width: 800px; width: 100%;
      border-radius: 20px;
      box-shadow: 0 10px 40px rgba(0,0,0,0.12);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      height: 90vh;
    }
    .chat-header {
      background: #163b33;
      color: #fff;
      text-align: center;
      padding: 18px;
      font-size: 20px;
      font-weight: bold;
      letter-spacing: 1px;
    }
    .chat-window {
      flex: 1;
      padding: 20px;
      overflow-y: auto;
      background: #fafafa;
    }
    .message {
      max-width: 75%;
      padding: 14px 18px;
      margin: 12px 0;
      border-radius: 18px;
      line-height: 1.5;
      animation: fadeIn .5s ease;
    }
    .bot {
      background: #1c3c34;
      color: #fff;
      border-radius: 18px 18px 18px 6px;
    }
    .user {
      background: #f0f0f0;
      color: #111;
      border-radius: 18px 18px 6px 18px;
      margin-left: auto;
    }
    .chat-input {
      display: flex;
      padding: 14px;
      border-top: 1px solid #ddd;
      background: #fff;
    }
    .chat-input input {
      flex: 1;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 12px;
      font-size: 15px;
    }
    .chat-input button {
      margin-left: 10px;
      background: #d4af37;
      border: none;
      color: #111;
      font-weight: bold;
      padding: 12px 20px;
      border-radius: 12px;
      cursor: pointer;
      transition: 0.3s;
    }
    .chat-input button:hover {
      background: #c19c2b;
    }
    @keyframes fadeIn {from {opacity:0;transform:translateY(12px);}to{opacity:1;transform:none;}}
    .fragrance-card {
      background: #fff;
      border: 2px solid #d4af37;
      padding: 20px;
      border-radius: 16px;
      margin-top: 20px;
      animation: fadeIn 1s ease;
    }
    .fragrance-card h3 {
      margin: 0 0 12px;
      color: #163b33;
    }
    .tag {
      display: inline-block;
      margin: 6px 6px 0 0;
      padding: 8px 12px;
      border-radius: 10px;
      background: #fafafa;
      border: 1px solid #eee;
    }
  </style>
</head>
<body>

<div class="chat-container">
  <div class="chat-header">✨ Test Olfativo SCENTIA AI ✨</div>
  <div id="chat-window" class="chat-window">
    <div class="message bot">👋 Hola, soy SCENTIA AI. Vamos a crear tu fragancia personalizada. ¿Cómo describirías tu personalidad?</div>
  </div>
  <div class="chat-input">
    <input id="user-input" type="text" placeholder="Escribe tu respuesta...">
    <button id="send-btn">Enviar</button>
  </div>
</div>

<script>
  const chatWindow = document.getElementById("chat-window");
  const userInput = document.getElementById("user-input");
  const sendBtn = document.getElementById("send-btn");

  const questions = [
    "¿Qué aromas te gustan más? (cítricos, florales, amaderados, dulces...)",
    "¿Prefieres fragancias suaves o intensas?",
    "¿En qué ocasión usarías este perfume?",
    "Cuéntame una breve historia que te defina."
  ];

  let answers = [];
  let currentQuestion = 0;

  function addMessage(text, sender="bot") {
    const msg = document.createElement("div");
    msg.className = "message " + sender;
    msg.innerText = text;
    chatWindow.appendChild(msg);
    chatWindow.scrollTop = chatWindow.scrollHeight;
  }

  function botAskNext() {
    if(currentQuestion < questions.length){
      setTimeout(()=> addMessage(questions[currentQuestion], "bot"), 600);
    } else {
      showResult();
    }
  }

  function showResult() {
    setTimeout(()=>{
      const card = document.createElement("div");
      card.className = "fragrance-card";
      card.innerHTML = `
        <h3>🌿 Tu Fragancia SCENTIA 🌿</h3>
        <p>Basado en lo que me contaste, he diseñado un perfume que refleja tu personalidad <strong>${answers[0]}</strong>, 
        con notas <strong>${answers[1]}</strong>, una intensidad <strong>${answers[2]}</strong>, perfecto para <strong>${answers[3]}</strong>.</p>
        <p><em>Tu historia añade un toque único: "${answers[4]}"</em></p>
        <div class="tag">Bergamota</div>
        <div class="tag">Jazmín</div>
        <div class="tag">Sándalo</div>
        <p style="margin-top:10px;font-style:italic;color:#777;">✨ Nombre sugerido: "Aura Privée"</p>
      `;
      chatWindow.appendChild(card);
      chatWindow.scrollTop = chatWindow.scrollHeight;
    }, 800);
  }

  sendBtn.addEventListener("click", ()=>{
    const text = userInput.value.trim();
    if(!text) return;
    addMessage(text, "user");
    answers.push(text);
    userInput.value = "";
    currentQuestion++;
    botAskNext();
  });

  userInput.addEventListener("keypress", e=>{
    if(e.key==="Enter"){ 
      e.preventDefault(); 
      sendBtn.click(); 
    }
  });
</script>

</body>
</html>
