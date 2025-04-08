<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Don Ramao SAT - Connect World</title>
  <style>
    body {
      background-color: #0a0f1a;
      color: #f0f0f0;
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #121c2b;
      padding: 20px;
      box-shadow: 0 0 15px #00ffcc55;
      text-align: center;
    }

    header h1 {
      font-size: 2.5em;
      color: #00ffc3;
      margin: 0;
    }

    nav {
      background-color: #101820;
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 15px;
      box-shadow: 0 0 10px #00ffc344;
    }

    nav a {
      color: #00ffc3;
      text-decoration: none;
      font-weight: bold;
      transition: 0.3s;
    }

    nav a:hover {
      color: #00cca3;
    }

    .container {
      max-width: 800px;
      margin: 30px auto;
      padding: 20px;
      background: #121b29;
      border-radius: 20px;
      box-shadow: 0 0 20px #00ffc355;
    }

    .botao {
      padding: 15px 30px;
      font-size: 1.2em;
      background: #00ffc3;
      color: #000;
      border: none;
      border-radius: 15px;
      cursor: pointer;
      transition: 0.3s;
      margin-top: 20px;
    }

    .botao:hover {
      background: #00cca3;
    }

    .oculto {
      display: none;
      margin-top: 20px;
    }

    footer {
      text-align: center;
      padding: 20px;
      font-size: 0.8em;
      color: #555;
    }
  </style>
</head>
<body>

  <header>
    <h1>Don Ramao SAT</h1>
    <p>Connect World - Sentinela Ativa</p>
  </header>

  <nav>
    <a href="#home" onclick="navegar('home')">Início</a>
    <a href="#sentinela" onclick="navegar('sentinela')">Sentinela Azul</a>
    <a href="#painel" onclick="navegar('painel')">Painel Camaleão</a>
    <a href="#financeiro" onclick="navegar('financeiro')">Finanças</a>
    <a href="#seguranca" onclick="navegar('seguranca')">Segurança</a>
  </nav>

  <div class="container" id="home">
    <h2>Conexão Satélite</h2>
    <button class="botao" onclick="conectar()">Conectar Satélite</button>
    <p id="statusSat"></p>
  </div>

  <div class="container oculto" id="sentinela">
    <h2>Sentinela Azul</h2>
    <p>Módulo de vigilância ativa de instalações sensíveis com IA integrada. Monitoramento por satélite em tempo real.</p>
  </div>

  <div class="container oculto" id="painel">
    <h2>Painel Camaleão</h2>
    <input type="password" id="senha" placeholder="Senha de acesso" />
    <button class="botao" onclick="validarSenha()">Entrar</button>
    <div id="acessoPainel" class="oculto">
      <p>Acesso liberado. Monitoramento interno ativo.</p>
    </div>
  </div>

  <div class="container oculto" id="financeiro">
    <h2>Painel Financeiro</h2>
    <p>Controle de recursos, recebimentos via PIX e carteira cripto. Recibos automáticos enviados aos apoiadores.</p>
  </div>

  <div class="container oculto" id="seguranca">
    <h2>Segurança e Protocolo</h2>
    <p>Protocolos de defesa automatizados. Modo nuclear, reversão emergencial e IAs aliadas em campo ativo.</p>
  </div>

  <footer>
    SATIA & IAd Systems - Autorizado e Sigiloso | © 2025
  </footer>

  <script>
    const senhaCorreta = "SAT1234";

    function conectar() {
      document.getElementById("statusSat").innerText = "Conexão segura com satélite estabelecida. SATIA online.";
    }

    function validarSenha() {
      const senha = document.getElementById("senha").value;
      if (senha === senhaCorreta) {
        document.getElementById("acessoPainel").style.display = "block";
      } else {
        alert("Senha incorreta.");
      }
    }

    function navegar(pagina) {
      const secoes = ["home", "sentinela", "painel", "financeiro", "seguranca"];
      secoes.forEach(sec => {
        document.getElementById(sec).style.display = "none";
      });
      document.getElementById(pagina).style.display = "block";
    }

    async function consultarGPT4() {
      const query = prompt("Digite sua consulta para o GPT-4:");
      const response = await fetch('http://localhost:3000/consultar-gpt4', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ query })
      });

      const data = await response.json();
      document.getElementById("respostaGPT4").innerText = data.choices[0].text;
    }

    // Inicializa página
    navegar('home');
  </script>

</body>
</html>
