<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Reserva - Hotel Santa Luz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      background-color: #f4f4f4;
      color: #333;
    }
    h1, h2 {
      text-align: center;
    }
    form {
      max-width: 600px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
    }
    input, select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      margin-top: 15px;
      padding: 10px;
      width: 48%;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
    }
    .btn-email {
      background-color: #004080;
      color: #fff;
    }
    .btn-whatsapp {
      background-color: #25D366;
      color: #fff;
      float: right;
    }
    @media (max-width: 600px) {
      button {
        width: 100%;
        margin-bottom: 10px;
      }
    }
  </style>
</head>
<body>
  <h1>Reserva - Hotel Santa Luz</h1>
  <form id="reserva-form">
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" required>
    
    <label for="checkin">Check-in:</label>
    <input type="date" id="checkin" name="checkin" required>
    
    <label for="checkout">Check-out:</label>
    <input type="date" id="checkout" name="checkout" required>
    
    <label for="num-pessoas">Número de Pessoas:</label>
    <input type="number" id="num-pessoas" name="num-pessoas" min="1" required>
    
    <label for="tipo-quarto">Tipo de Quarto:</label>
    <select id="tipo-quarto" name="tipo-quarto" required>
      <option value="casal">Casal</option>
      <option value="familia">Família (até 5 pessoas)</option>
      <option value="triplo">Triplo</option>
      <option value="quadruplo">Quádruplo</option>
    </select>
    
    <label for="contato">Contato (Telefone ou E-mail):</label>
    <input type="text" id="contato" name="contato" required>
    
    <div style="overflow: auto;">
      <button type="button" class="btn-email" onclick="enviarEmail()">Enviar Reserva por E-mail</button>
      <button type="button" class="btn-whatsapp" onclick="enviarWhatsApp()">Compartilhar via WhatsApp</button>
    </div>
  </form>
  
  <script>
    function enviarEmail() {
      var nome = document.getElementById("nome").value;
      var checkin = document.getElementById("checkin").value;
      var checkout = document.getElementById("checkout").value;
      var numPessoas = document.getElementById("num-pessoas").value;
      var tipoQuarto = document.getElementById("tipo-quarto").value;
      var contato = document.getElementById("contato").value;
      
      var subject = "Reserva - " + nome;
      var body = "Nome: " + nome + "\n" +
                 "Check-in: " + checkin + "\n" +
                 "Check-out: " + checkout + "\n" +
                 "Número de pessoas: " + numPessoas + "\n" +
                 "Tipo de quarto: " + tipoQuarto + "\n" +
                 "Contato: " + contato;
      
      var mailto_link = "mailto:hotelsantaluz@gmail.com" +
                        "?subject=" + encodeURIComponent(subject) +
                        "&body=" + encodeURIComponent(body);
      window.location.href = mailto_link;
    }
    
    function enviarWhatsApp() {
      var nome = document.getElementById("nome").value;
      var checkin = document.getElementById("checkin").value;
      var checkout = document.getElementById("checkout").value;
      var numPessoas = document.getElementById("num-pessoas").value;
      var tipoQuarto = document.getElementById("tipo-quarto").value;
      var contato = document.getElementById("contato").value;
      
      var message = "Reserva de Hospedagem:%0A" +
                    "Nome: " + nome + "%0A" +
                    "Check-in: " + checkin + "%0A" +
                    "Check-out: " + checkout + "%0A" +
                    "Número de pessoas: " + numPessoas + "%0A" +
                    "Tipo de quarto: " + tipoQuarto + "%0A" +
                    "Contato: " + contato;
      
      var phone = "5512996180635"; // Número do hotel com código do país (Brasil = 55)
      var url = "https://wa.me/" + phone + "?text=" + encodeURIComponent(message);
      window.open(url, "_blank");
    }
  </script>
</body>
</html>
