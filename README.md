<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Renewable Energy Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .calculator {
            max-width: 500px;
            margin: 0 auto;
        }
        label, input {
            display: block;
            margin-bottom: 10px;
        }
        .result {
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <h1>Renewable Energy Power Calculator</h1>

        <h2>Solar Power Calculation</h2>
        <label for="solarArea">Solar Panel Area (m²):</label>
        <input type="number" id="solarArea" placeholder="Enter area in square meters">

        <label for="sunlightHours">Hours of Sunlight:</label>
        <input type="number" id="sunlightHours" placeholder="Enter hours of sunlight">

        <button onclick="calculateSolarPower()">Calculate Solar Power</button>
        <div class="result" id="solarResult"></div>

        <h2>Wind Power Calculation</h2>
        <label for="bladeRadius">Wind Turbine Blade Radius (m):</label>
        <input type="number" id="bladeRadius" placeholder="Enter blade radius in meters">

        <label for="windSpeed">Wind Speed (m/s):</label>
        <input type="number" id="windSpeed" placeholder="Enter wind speed in meters per second">

        <label for="windHours">Hours of Wind:</label>
        <input type="number" id="windHours" placeholder="Enter hours of wind">

        <button onclick="calculateWindPower()">Calculate Wind Power</button>
        <div class="result" id="windResult"></div>
    </div>

    <script>
     
        const SOLAR_PANEL_EFFICIENCY = 0.20; 
        const SOLAR_INSOLATION = 5;  
        const AIR_DENSITY = 1.225; 
        const WIND_TURBINE_EFFICIENCY = 0.40; 

        
        function calculateSolarPower() {
            const area = parseFloat(document.getElementById("solarArea").value);
            const hours = parseFloat(document.getElementById("sunlightHours").value);

            if (isNaN(area) || isNaN(hours)) {
                document.getElementById("solarResult").innerHTML = "Please enter valid inputs for solar power.";
                return;
            }

           
            const solarPower = area * SOLAR_INSOLATION * SOLAR_PANEL_EFFICIENCY * hours;
            document.getElementById("solarResult").innerHTML = Solar Power Generated: ${solarPower.toFixed(2)} kWh;
        }

       
        function calculateWindPower() {
            const radius = parseFloat(document.getElementById("bladeRadius").value);
            const windSpeed = parseFloat(document.getElementById("windSpeed").value);
            const hours = parseFloat(document.getElementById("windHours").value);

            if (isNaN(radius) || isNaN(windSpeed) || isNaN(hours)) {
                document.getElementById("windResult").innerHTML = "Please enter valid inputs for wind power.";
                return;
            }

            const sweptArea = Math.PI * Math.pow(radius, 2);  
            const windPower = 0.5 * AIR_DENSITY * sweptArea * Math.pow(windSpeed, 3) * WIND_TURBINE_EFFICIENCY * hours;
            document.getElementById("windResult").innerHTML = Wind Power Generated: ${windPower.toFixed(2)} kWh;
        }
    </script>
</body>
</html>
