<!DOCTYPE html> 
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz Ano Novo 2025!</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      text-align: center;
      background: linear-gradient(to bottom, #001f3f, #001d42, #00284e);
      color: #ffffff;
      padding: 20px;
    }
    .hidden {
      display: none;
    }
    button {
      background-color: #ffd700;
      color: #000;
      padding: 12px 25px;
      border: none;
      cursor: pointer;
      border-radius: 25px;
      font-weight: bold;
      box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
    }
    button:hover {
      background-color: #ffcc00;
    }
    .form-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 30px;
    }
    .input-container {
      position: relative;
      margin-bottom: 15px;
    }
    input {
      padding: 10px;
      width: 250px;
      font-size: 16px;
      border-radius: 25px;
      border: 1px solid #ccc;
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
      text-align: center;
    }
    .toggle-password {
      position: absolute;
      right: -0px; /* Movido cerca de 2 cm para a direita */
      top: 50%;
      transform: translateY(-50%);
      cursor: pointer;
      background: none;
      border: none;
      color: #ffd700;
      font-size: 18px;
    }
    #message h2 {
      font-size: 36px;
      margin-bottom: 25px;
      color: #ffcc00;
    }
    #message p {
      font-size: 20px;
      text-align: justify;
      margin: 20px auto;
      max-width: 600px;
      line-height: 1.6;
    }
    .intro h1 {
      font-size: 48px;
      color: #ffcc00;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }
    .intro p {
      font-size: 20px;
      margin-top: 10px;
    }
  </style>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" />
</head>
<body>
  <div id="intro" class="intro">
    <h1>🎆 Feliz Ano Novo!! 🎆</h1>
    <p>Insira seu nome e senha para receber sua mensagem personalizada:</p>
  </div>
  <form id="loginForm" class="form-container">
    <div class="input-container">
      <input type="text" id="name" placeholder="Seu nome" required>
    </div>
    <div class="input-container">
      <input type="password" id="password" placeholder="Senha" required>
      <button type="button" class="toggle-password">
        <i class="fas fa-eye"></i>
      </button>
    </div>
    <button type="submit">Entrar</button>
  </form>
  
  <div id="message" class="hidden">
    <h2>Mensagem para <span id="userName"></span></h2>
    <p id="userMessage"></p>
  </div>
  
  <script>
    // Função para salvar novos usuários com mensagens
    function saveUser(name, password, message) {
      const users = JSON.parse(localStorage.getItem('users')) || {};
      users[name] = { password, message };
      localStorage.setItem('users', JSON.stringify(users));
    }

    // Função para verificar se o nome e senha estão corretos
    function validateUser(name, password) {
      const users = JSON.parse(localStorage.getItem('users')) || {};
      if (users[name] && users[name].password === password) {
        return users[name].message;
      }
      return null;
    }

    // Adicionando os dados de usuários no LocalStorage com mensagens personalizadas
    saveUser("Marina", "Mahzinha2107", "Mahzinha, feliz ano novo!! Eu tenho tantas coisas para te falar, mas vou simplificar as coisas. Obrigado por fazer parte do meu 2024, você me ajudou muito nesse ano, sua companhia faz muito bem, você foi uma dos motivos para meu ano ter sido muito melhor, espero que para você eu tenha feito algo significante para fazê-lo minimante melhor. Bom, que 2025 seja repleto de momentos incríveis, que ele der oportunidades para você melhorar internamente e externamente.");
    saveUser("Mariany", "Mary2107", "Mary, feliz ano novo!! Obrigado por fazer parte do meu 2024, você foi uma dos motivos para meu ano ter sido muito melhor. Gosto muito das nossas interações, bom, que 2025 seja repleto de momentos incríveis que ele te der oportunidades para você melhorar internamente e externamente.");
    saveUser("Geovani", "Geo0712", "Geo, feliz ano novo, foi um prazer contar contigo durante o ano, nossa amizade é mais firme que aço reforçado, gratidão por tudo meu mano!! Que 2025 seja repleto de oportunidades e que você tem ótimas experiencias esse ano, você merece.");
    saveUser("Laura", "Laurinha0404", "Feliz ano novo Laura!! Foi incrível passar boa parte contigo esse ano, mesmo que tenha sido na escola estudando, mas foi o teu jeito estressadinha, simpática e tagarela que fez desse ambiente melhor. Bom, feliz 2025, que ótimas oportunidades venhas para o seu crescimento pessoal.");
    saveUser("Sarah", "Sah2905", "Feliz ano novo, Sahh!! Tem teu jeitinho meio estressada, mas às vezes é isso que nos tiras boas risadas ou momentos que geraram felicidades, além dos estresses e perrengues que passamos nos trabalhos, etc. Que 2025 possa nos proporcionar muitos momentos como esses, mas tirando a parte do estresse séria bom né?! Em fim, que 2025 venha e traga diversas oportunidades para você evoluir como ser humano.");

    // Alternar a visibilidade da senha
    document.querySelector(".toggle-password").addEventListener("click", function() {
      const passwordField = document.getElementById("password");
      const type = passwordField.type === "password" ? "text" : "password";
      passwordField.type = type;
    });

    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const name = document.getElementById("name").value;
      const password = document.getElementById("password").value;

      const message = validateUser(name, password);
      if (message) {
        // Mostrar mensagem personalizada
        document.getElementById("userName").textContent = name;
        document.getElementById("userMessage").textContent = message;

        // Ocultar o formulário e introdução
        document.getElementById("intro").remove();
        document.getElementById("loginForm").remove();
        document.getElementById("message").classList.remove("hidden");
      } else {
        alert("Nome ou senha incorretos! Tente novamente.");
      }
    });
  </script>
</body>
</html>
