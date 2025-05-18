<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Chatbot - Queda Capilar e Nutrição</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="chat-container">
        <h2>Chatbot de Avaliação Nutricional e Queda Capilar</h2>
        <div id="chat-box"></div>
        <input type="text" id="user-input" placeholder="Digite sua resposta..." autofocus />
        <button onclick="sendMessage()">Enviar</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f2f2f2;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}
.chat-container {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    width: 400px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
#chat-box {
    border: 1px solid #ccc;
    padding: 10px;
    height: 300px;
    overflow-y: auto;
    margin-bottom: 10px;
    background-color: #fafafa;
}
input, button {
    padding: 10px;
    width: calc(100% - 22px);
    margin-bottom: 10px;
    box-sizing: border-box;
}
button {
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}
button:hover {
    background-color: #45a049;
}
const questions = [
    "Você já foi diagnosticada com alguma deficiência nutricional? (Ex: Anemia ferropriva, deficiência de B12, ferro ou vitamina D)",
    "Você sofre ou já sofreu com queda de cabelo? (Sim, atualmente / Sim, já sofri / Não / Não me recordo)",
    "Há quanto tempo você percebe a queda capilar? (Menos de 6 meses / 6 meses a 1 ano / Mais de 1 ano / Não me recordo)",
    "A queda de cabelo foi diagnosticada por um profissional? (Sim / Procurei ajuda, mas sem diagnóstico / Não procurei ajuda)",
    "Algum profissional mencionou relação com alimentação ou deficiência nutricional? (Sim / Não / Não consultei)",
    "Com que frequência consome alimentos ricos em ferro, zinco, e vitaminas do complexo B? (Sempre / Às vezes / Nunca)",
    "Você faz uso de suplementos alimentares? (Sim, diariamente / Sim, ocasionalmente / Não)"
];

const responses = [];
let currentQuestion = 0;

function sendMessage() {
    const input = document.getElementById('user-input');
    const chatBox = document.getElementById('chat-box');
    const userText = input.value.trim();
    if (userText === "") return;

    chatBox.innerHTML += "<p><strong>Você:</strong> " + userText + "</p>";
    responses.push(userText);
    input.value = "";
    currentQuestion++;

    if (currentQuestion < questions.length) {
        setTimeout(() => {
            chatBox.innerHTML += "<p><strong>Chatbot:</strong> " + questions[currentQuestion] + "</p>";
            chatBox.scrollTop = chatBox.scrollHeight;
        }, 500);
    } else {
        setTimeout(() => {
            chatBox.innerHTML += "<p><strong>Chatbot:</strong> Obrigado pelas respostas. Com base nelas, recomendamos procurar um nutricionista ou dermatologista para uma avaliação completa.</p>";
            chatBox.scrollTop = chatBox.scrollHeight;
        }, 500);
    }
}

window.onload = () => {
    document.getElementById('chat-box').innerHTML = "<p><strong>Chatbot:</strong> " + questions[0] + "</p>";
};
