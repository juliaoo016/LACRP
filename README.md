<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LAKJCSRP - Loja de Coins</title>
  <style>
    body {
      font-family: 'Arial Black', sans-serif;
      background: url('https://wallpapercave.com/wp/wp1839577.jpg') no-repeat center center fixed;
      background-size: cover;
      color: white;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: rgba(0,0,0,0.8);
      padding: 20px;
      text-align: center;
      border-bottom: 3px solid #00ffcc;
    }
    header h1 {
      margin: 0;
      color: #00ffcc;
      font-size: 36px;
    }
    .container {
      padding: 20px;
      max-width: 800px;
      margin: auto;
      background-color: rgba(0, 0, 0, 0.7);
      border-radius: 10px;
    }
    .form-section {
      margin-bottom: 30px;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border-radius: 5px;
      border: none;
      font-size: 16px;
    }
    .btn {
      background-color: #00ffcc;
      border: none;
      padding: 10px 20px;
      color: #000;
      font-weight: bold;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 15px;
    }
    .btn:hover {
      background-color: #00e6b8;
    }
    footer {
      background-color: rgba(0,0,0,0.8);
      color: #aaa;
      text-align: center;
      padding: 10px;
      margin-top: 40px;
    }
    .contact {
      text-align: center;
      margin-top: 20px;
    }
    .pix-box {
      background-color: #111;
      padding: 15px;
      border-radius: 10px;
      margin-top: 20px;
    }
  </style>
  <script>
    function atualizarPreco() {
      const quantidade = document.getElementById('quantidade').value;
      const preco = parseInt(quantidade) * 1;
      document.getElementById('valor-total').innerText = `Total: R$ ${preco},00`;
      document.getElementById('pix-info').style.display = 'block';
    }

    function enviarWhatsApp() {
      const nick = document.getElementById('nickname').value.trim();
      const quantidade = document.getElementById('quantidade').value;

      if (!nick) {
        alert('Por favor, insira seu nick.');
        return;
      }

      const mensagem = `Olá, já realizei o pagamento via PIX. Meu nick: ${nick} | Quantidade: ${quantidade} coins`;
      const url = `https://wa.me/5516991301319?text=${encodeURIComponent(mensagem)}`;
      window.open(url, '_blank');
    }
  </script>
</head>
<body>
  <header>
    <h1>LAKJCSRP</h1>
    <p>Compre suas coins para Los Angeles Crimes (LAK)</p>
  </header>
  <div class="container">
    <div class="form-section">
      <label for="nickname">Insira seu Nick do Jogo:</label>
      <input type="text" id="nickname" name="nickname" required />

      <label for="quantidade">Escolha a quantidade de coins (máximo 50):</label>
      <select id="quantidade" name="quantidade" onchange="atualizarPreco()" required>
        <option value="" disabled selected>Selecione</option>
        ${[...range(1, 51)].map(v => f'<option value="{v}">{v} Coin(s)</option>').join('')}
      </select>

      <div class="pix-box" id="pix-info" style="display:none;">
        <h3 id="valor-total">Total: R$ 0,00</h3>
        <p><strong>Chave PIX:</strong> juliocesarsouza656@gmail.com</p>
        <p>Após o pagamento, envie o comprovante e seu nick via WhatsApp.</p>
        <button class="btn" onclick="enviarWhatsApp()">Enviar Comprovante no WhatsApp</button>
      </div>
    </div>

    <div class="contact">
      <h3>Suporte:</h3>
      <p><a href="https://wa.me/5516991301319" style="color: #00ffcc">WhatsApp: (16) 99130-1319</a></p>
    </div>
  </div>
  <footer>
    <p>LAKJCSRP &copy; 2025 - Todos os direitos reservados.</p>
  </footer>
</body>
</html>
