<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Калькулятор углеродного следа</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
      background-color: #f4f4f9;
    }
    .container {
      max-width: 500px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    input[type="number"] {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      padding: 10px 20px;
      background-color: #4caf50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Калькулятор углеродного следа</h1>
    <form id="carbonCalculator">
      <label for="fuel">Потребление топлива (литров в месяц):</label>
      <input type="number" id="fuel" placeholder="Введите количество литров">
      
      <label for="electricity">Электроэнергия (кВт·ч в месяц):</label>
      <input type="number" id="electricity" placeholder="Введите количество кВт·ч">
      
      <label for="flights">Количество авиаперелетов (в год):</label>
      <input type="number" id="flights" placeholder="Введите количество перелетов">
      
      <button type="button" onclick="calculateCarbonFootprint()">Рассчитать</button>
    </form>
    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateCarbonFootprint() {
      const fuel = parseFloat(document.getElementById("fuel").value) || 0;
      const electricity = parseFloat(document.getElementById("electricity").value) || 0;
      const flights = parseInt(document.getElementById("flights").value) || 0;

      const fuelEmissionFactor = 2.31;
      const electricityEmissionFactor = 0.5;
      const flightEmissionFactor = 250;

      const fuelEmissions = fuel * fuelEmissionFactor;
      const electricityEmissions = electricity * electricityEmissionFactor;
      const flightEmissions = flights * flightEmissionFactor;

      const totalEmissions = fuelEmissions + electricityEmissions + flightEmissions;

      const resultDiv = document.getElementById("result");
      resultDiv.innerHTML = `
        Ваш углеродный след: <strong>${totalEmissions.toFixed(2)} кг CO₂</strong>.
      `;
    }
  </script>
</body>
</html>
