# calculadora-recortes
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Recortes</title>
  <link href="https://fonts.googleapis.com/css?family=Montserrat:400,700|Playfair+Display:700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(to right, #ff9a9e, #fad0c4);
      margin: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .container {
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      max-width: 400px;
      width: 100%;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    }
    h2 {
      color: #ff6f91;
      text-align: center;
      margin-bottom: 20px;
      font-family: 'Playfair Display', serif;
    }
    label {
      display: block;
      font-size: 16px;
      margin-bottom: 5px;
      color: #555;
      font-weight: bold;
    }
    input[type="number"] {
      width: 100%;
      padding: 12px;
      margin-bottom: 15px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
      transition: border-color 0.3s ease;
    }
    input[type="number"]:focus {
      border-color: #ff6f91;
      outline: none;
    }
    button {
      width: 100%;
      padding: 12px;
      background-color: #ff6f91;
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 18px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #ff3b7f;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
      color: #333;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Calculadora de Recortes</h2>
    <label for="originalWidth">Largura da Folha Original (cm):</label>
    <input type="number" id="originalWidth" placeholder="Ex: 100">
    
    <label for="originalHeight">Altura da Folha Original (cm):</label>
    <input type="number" id="originalHeight" placeholder="Ex: 50">
    
    <label for="cutWidth">Largura da Folha a ser cortada (cm):</label>
    <input type="number" id="cutWidth" placeholder="Ex: 10">
    
    <label for="cutHeight">Altura da Folha a ser cortada (cm):</label>
    <input type="number" id="cutHeight" placeholder="Ex: 5">
    
    <button onclick="calcularRecortes()">Calcular</button>
    
    <div class="result" id="result"></div>
  </div>

  <script>
    function calcularRecortes() {
      const originalWidth = parseFloat(document.getElementById('originalWidth').value);
      const originalHeight = parseFloat(document.getElementById('originalHeight').value);
      const cutWidth = parseFloat(document.getElementById('cutWidth').value);
      const cutHeight = parseFloat(document.getElementById('cutHeight').value);

      if (isNaN(originalWidth) || isNaN(originalHeight) || isNaN(cutWidth) || isNaN(cutHeight) ||
          originalWidth <= 0 || originalHeight <= 0 || cutWidth <= 0 || cutHeight <= 0) {
        document.getElementById('result').innerText = 'Por favor, insira valores válidos e maiores que zero.';
        return;
      }

      const numHorizontal = Math.floor(originalWidth / cutWidth);
      const numVertical = Math.floor(originalHeight / cutHeight);
      const total = numHorizontal * numVertical;

      document.getElementById('result').innerHTML = `
        <p>Recortes na horizontal: ${numHorizontal}</p>
        <p>Recortes na vertical: ${numVertical}</p>
        <p>Total de recortes possíveis: ${total}</p>
      `;
    }
  </script>
</body>
</html>
