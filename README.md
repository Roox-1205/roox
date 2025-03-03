<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .weather-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            display: inline-block;
        }
        img {
            width: 100px;
        }
    </style>
</head>
<body>

    <h2>Weather App</h2>
    <input type="text" id="city" placeholder="Enter city name">
    <button onclick="getWeather()">Get Weather</button>

    <div id="weather" class="weather-container" style="display:none;">
        <h3 id="city-name"></h3>
        <img id="weather-icon" src="" alt="Weather Icon">
        <p id="temperature"></p>
        <p id="description"></p>
    </div>

    <script>
        async function getWeather() {
            const city = document.getElementById('city').value;
            const apiKey = "YOUR_API_KEY";
            const url = https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey};

            try {
                const response = await fetch(url);
                const data = await response.json();

                if (data.cod !== 200) {
                    alert(data.message);
                    return;
                }

                document.getElementById('weather').style.display = "block";
                document.getElementById('city-name').innerText = data.name;
                document.getElementById('temperature').innerText = Temperature: ${data.main.temp}°C;
                document.getElementById('description').innerText = Weather: ${data.weather[0].description};
                document.getElementById('weather-icon').src = https://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png;

            } catch (error) {
                alert("Error fetching weather data.");
                console.error(error);
            }
        }
    </script>

</body>
</html>
