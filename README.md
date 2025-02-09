<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Weather Website</title>
  <!-- Material Icons -->
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet" />
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f0f0f0;
    }
    .container {
      max-width: 900px;
      margin: 50px auto;
      background-color: #fff;
      padding: 20px;
      border: 1px solid #ccc;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
    /* Header: Weather Title and Settings Button */
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }
    .weather-title {
      font-size: 1.5em;
      color: #888;
    }
    #settings-btn {
      cursor: pointer;
      display: flex;
      align-items: center;
      color: black;
      font-size: 1em;
    }
    #settings-btn .material-icons {
      margin-right: 5px;
      font-size: 24px;
      color: black;
    }
    .search-box,
    #fetch-location-btn,
    #unit-dropdown,
    #follow-me-dropdown,
    #whatsnew-dropdown {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      border: 1px solid #ccc;
      font-size: 16px;
      border-radius: 0;
    }
    /* Inline dropdowns */
    #unit-dropdown,
    #follow-me-dropdown,
    #whatsnew-dropdown {
      width: auto;
      display: inline-block;
      margin-right: 10px;
    }
    #fetch-location-btn {
      background-color: orange;
      color: white;
      cursor: pointer;
    }
    .search-results {
      max-height: 200px;
      overflow-y: auto;
      border: 1px solid #ccc;
      background-color: white;
      position: absolute;
      width: 100%;
      border-radius: 0;
      z-index: 500;
    }
    .search-results div {
      padding: 10px;
      cursor: pointer;
    }
    .search-results div:hover {
      background-color: #f0f0f0;
    }
    .weather-info {
      text-align: center;
    }
    .weather-icon {
      width: 100px;
    }
    .temp {
      font-size: 2em;
      font-weight: bold;
    }
    .real-feel {
      font-size: 0.9em;
      color: #555;
    }
    .details {
      margin-top: 20px;
    }
    .details div {
      margin: 5px 0;
    }
    .error-message {
      color: red;
      text-align: center;
    }
    .hourly-forecast {
      margin-top: 30px;
    }
    .hourly-forecast-list {
      width: 100%;
    }
    .hourly-forecast-title {
      font-size: 1.2em;
      font-weight: bold;
      margin-bottom: 10px;
    }
    .hourly-item {
      display: flex;
      justify-content: space-between;
      padding: 10px 0;
      border-top: 1px solid #ccc;
    }
    .hourly-item:first-child {
      border-top: none;
    }
    .hourly-item div {
      display: inline-block;
    }
    .hourly-item .hour-time {
      width: 30%;
    }
    .hourly-item .hour-details {
      width: 50%;
      display: flex;
      align-items: center;
    }
    .hourly-item .hour-temperature {
      width: 20%;
      text-align: right;
    }
    /* Radar Embed */
    #radar-embed {
      margin: 20px 0;
    }
    /* Popup Styles with Fade Transitions */
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.5s ease;
    }
    .overlay.show {
      opacity: 1;
      pointer-events: all;
    }
    .popup {
      background-color: white;
      padding: 20px;
      border-radius: 0;
      width: 90%;
      max-width: 500px;
      text-align: left;
      position: relative;
      opacity: 0;
      transition: opacity 0.5s ease;
    }
    .overlay.show .popup {
      opacity: 1;
    }
    .popup .close-btn {
      position: absolute;
      top: 5px;
      right: 10px;
      background: none;
      border: none;
      font-size: 1.2em;
      cursor: pointer;
      color: black;
    }
    .popup h2 {
      margin: 0;
      font-size: 1.2em;
      color: #333;
    }
    .popup p {
      font-size: 0.9em;
      color: #555;
    }
    .popup .release-date {
      font-size: 0.8em;
      color: #888;
      margin-bottom: 10px;
    }
    .popup button {
      padding: 10px;
      margin: 10px 0 0 0;
      border: 1px solid #ccc;
      background-color: orange;
      color: white;
      cursor: pointer;
      border-radius: 0;
    }
    .popup .cancel-btn {
      background-color: #ccc;
    }
    footer {
      text-align: center;
      margin-top: 30px;
      font-size: 12px;
      color: #aaa;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header">
    <div class="weather-title">Weather</div>
    <div id="settings-btn" onclick="showSettingsPopup()">
      <i class="material-icons">settings</i>
      <span>Settings</span>
    </div>
  </div>
  <button id="fetch-location-btn" onclick="showLocationConsentPopup()">Fetch Current Location</button>
  <select id="unit-dropdown" onchange="updateWeatherUnit()">
    <option value="imperial">Fahrenheit (°F)</option>
    <option value="metric">Celsius (°C)</option>
  </select>
  <select id="follow-me-dropdown" onchange="followMe()">
    <option value="">Follow Me</option>
    <option value="YouTube">YouTube</option>
    <option value="Discord">Discord</option>
  </select>
  <select id="whatsnew-dropdown" onchange="handleWhatsNewChange()">
    <!-- Newest first (descending by date) -->
    <option value="">What's New</option>
    <option value='{"version":"2025.2.0.3", "description": "Updated consent issue.", "date": "2/9/2025"}'>2025.2.0.3</option>
    <option value='{"version":"2025.001.4.0", "description": "Added new features including search history, radar embed, improved error handling, and precipitation chance display.", "date": "2/8/2025"}'>2025.001.4.0</option>
  </select>
  <input type="text" class="search-box" id="city-input" placeholder="Enter city name" oninput="onSearchInput()" onkeydown="handleKeyDown(event)">
  <div id="search-results" class="search-results" style="display: none;"></div>

  <!-- Current Location Text -->
  <div id="current-location" style="text-align: center; font-size: 1.2em; margin-bottom: 15px;"></div>

  <div id="weather-result" class="weather-info">
    <!-- Weather info will be displayed here -->
  </div>
  
  <!-- Radar Embed -->
  <div id="radar-embed">
    <!-- Radar embed will appear here -->
  </div>
  
  <div class="error-message" id="error-message"></div>

  <div class="hourly-forecast">
    <div class="hourly-forecast-list" id="hourly-forecast">
      <!-- Hourly forecast will be displayed here -->
    </div>
  </div>

  <footer>(C) 2025 ToxicStudios - Do Not Distribute!</footer>
</div>

<!-- Popup Overlay for Location Consent -->
<div id="overlay" class="overlay">
  <div class="popup">
    <p>Do you consent to fetch your current location? <span style="font-size: 12px;">We do NOT track your location!</span></p>
    <div style="margin-bottom: 10px;">
      <input type="checkbox" id="never-ask" />
      <label for="never-ask">Never ask again</label>
    </div>
    <button onclick="acceptConsent()">Accept</button>
    <button class="cancel-btn" onclick="closePopup()">Cancel</button>
  </div>
</div>

<!-- Popup Overlay for What's New -->
<div id="whatsnew-overlay" class="overlay">
  <div class="popup" id="whatsnew-popup">
    <button class="close-btn" onclick="closeWhatsNewPopup()">X</button>
    <h2 id="changelog-title"></h2>
    <div class="release-date" id="release-date"></div>
    <p id="changelog-description"></p>
    <button onclick="closeWhatsNewPopup()">Close</button>
  </div>
</div>

<!-- Popup Overlay for Settings -->
<div id="settings-overlay" class="overlay">
  <div class="popup" id="settings-popup">
    <button class="close-btn" onclick="closeSettingsPopup()">X</button>
    <h2>Settings</h2>
    <button onclick="openFeedbackPopup()">FAQ / Feedback</button>
    <button onclick="openResetPopup()">Reset Permission</button>
  </div>
</div>

<!-- Popup Overlay for Feedback UI -->
<div id="feedback-overlay" class="overlay">
  <div class="popup" id="feedback-popup">
    <button class="close-btn" onclick="closeFeedbackPopup()">X</button>
    <h2>FAQ / Feedback</h2>
    <textarea id="feedback-text" placeholder="Enter your feedback (max 1000 characters)" maxlength="1000" style="width:100%; height:100px; resize: none;"></textarea>
    <button onclick="submitFeedback()">Submit</button>
    <button class="cancel-btn" onclick="closeFeedbackPopup()">Cancel</button>
  </div>
</div>

<!-- Popup Overlay for Reset Permission -->
<div id="reset-overlay" class="overlay">
  <div class="popup" id="reset-popup">
    <button class="close-btn" onclick="closeResetPopup()">X</button>
    <h2>Reset Permission</h2>
    <p>Are you sure you want to reset permissions? This will clear all saved data and permissions.</p>
    <button onclick="resetPermissions()">Accept</button>
    <button class="cancel-btn" onclick="closeResetPopup()">Cancel</button>
  </div>
</div>

<script>
  const apiKey = "7933e6835b69f299032f55f257098511"; // OpenWeather API key
  let userLocation = null;
  let unit = "imperial"; // Default unit (Fahrenheit)

  // --- Settings UI ---
  function showSettingsPopup() {
    document.getElementById("settings-overlay").classList.add("show");
  }
  function closeSettingsPopup() {
    document.getElementById("settings-overlay").classList.remove("show");
  }

  // --- Follow Me Dropdown ---
  function followMe() {
    const dropdown = document.getElementById("follow-me-dropdown");
    const selectedOption = dropdown.value;
    if (selectedOption === "YouTube") {
      window.open("https://www.youtube.com/@toxic5018.2", "_blank");
    } else if (selectedOption === "Discord") {
      window.open("https://discord.gg/qet79cugV6", "_blank");
    }
    dropdown.value = "";
  }

  // --- What's New Dropdown & Popup ---
  function handleWhatsNewChange() {
    const dropdown = document.getElementById("whatsnew-dropdown");
    const selectedValue = dropdown.value;
    if (selectedValue) {
      const info = JSON.parse(selectedValue);
      document.getElementById("changelog-title").innerText = "Changelog " + info.version;
      document.getElementById("release-date").innerText = "Release Date: " + info.date;
      document.getElementById("changelog-description").innerText = info.description;
      document.getElementById("whatsnew-overlay").classList.add("show");
    }
  }
  function closeWhatsNewPopup() {
    document.getElementById("whatsnew-overlay").classList.remove("show");
    document.getElementById("whatsnew-dropdown").value = "";
  }

  // --- Feedback UI ---
  function openFeedbackPopup() {
    document.getElementById("feedback-overlay").classList.add("show");
    closeSettingsPopup();
  }
  function closeFeedbackPopup() {
    document.getElementById("feedback-overlay").classList.remove("show");
    document.getElementById("feedback-text").value = "";
  }
  function formatTimestamp(date) {
    const month = (date.getMonth()+1).toString().padStart(2, '0');
    const day = date.getDate().toString().padStart(2, '0');
    const year = date.getFullYear();
    let hours = date.getHours();
    const minutes = date.getMinutes().toString().padStart(2, '0');
    const ampm = hours >= 12 ? 'PM' : 'AM';
    hours = hours % 12 || 12;
    return `${month}/${day}/${year} | ${hours}:${minutes} ${ampm}`;
  }
  async function submitFeedback() {
    const feedbackText = document.getElementById("feedback-text").value.trim();
    if (!feedbackText) {
      alert("Please enter your feedback.");
      return;
    }
    if (feedbackText.length > 1000) {
      alert("Feedback must be 1000 characters or less.");
      return;
    }
    const timestamp = formatTimestamp(new Date());
    try {
      const response = await fetch("https://toxicstudios-6de44-default-rtdb.firebaseio.com/Feedback.json", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ feedback: feedbackText, timestamp })
      });
      if (response.ok) {
        alert("Thank you for your feedback!");
        closeFeedbackPopup();
      } else {
        alert("There was an error submitting your feedback. Please try again later.");
      }
    } catch (error) {
      console.error("Error submitting feedback:", error);
      alert("Error submitting feedback. Please check your connection.");
    }
  }

  // --- Reset Permission UI ---
  function openResetPopup() {
    document.getElementById("reset-overlay").classList.add("show");
    closeSettingsPopup();
  }
  function closeResetPopup() {
    document.getElementById("reset-overlay").classList.remove("show");
  }
  function resetPermissions() {
    localStorage.removeItem("neverAskConsent");
    localStorage.removeItem("weatherSearchHistory");
    location.reload();
  }

  // --- Show No WiFi Error (using Material Icons) ---
  function showNoWifiError() {
    document.getElementById("error-message").innerHTML = `<i class="material-icons" style="display:block; margin-bottom:5px;">signal_wifi_off</i> No WiFi Connection`;
  }

  // --- Search History Handling ---
  function addToHistory(city) {
    let history = JSON.parse(localStorage.getItem("weatherSearchHistory") || "[]");
    const now = new Date().getTime();
    history.push({ city, timestamp: now });
    history = history.filter(item => now - item.timestamp < 86400000);
    localStorage.setItem("weatherSearchHistory", JSON.stringify(history));
  }
  function showHistory() {
    let history = JSON.parse(localStorage.getItem("weatherSearchHistory") || "[]");
    const now = new Date().getTime();
    history = history.filter(item => now - item.timestamp < 86400000);
    if (history.length === 0) {
      document.getElementById("search-results").style.display = "none";
      return;
    }
    const uniqueCities = [...new Set(history.map(item => item.city))];
    const resultsHTML = uniqueCities.map(city => `<div onclick="selectCity('${city}')">${city}</div>`).join('');
    document.getElementById("search-results").innerHTML = resultsHTML;
    document.getElementById("search-results").style.display = "block";
  }
  function onSearchInput() {
    const city = document.getElementById("city-input").value;
    if (city === "") {
      showHistory();
    } else {
      fetchSuggestions();
    }
  }

  // --- Handle Enter Key in Search Box ---
  function handleKeyDown(event) {
    if (event.key === 'Enter') {
      const city = document.getElementById("city-input").value;
      if (city) {
        fetchWeather(city);
      } else {
        fetchLocation();
      }
      document.getElementById("search-results").style.display = "none";
    }
  }

  // --- Select City from Suggestions or History ---
  function selectCity(cityName) {
    document.getElementById("city-input").value = cityName;
    document.getElementById("search-results").style.display = "none";
    fetchWeather(cityName);
  }

  // --- Popup Handling for Location Consent ---
  function showLocationConsentPopup() {
    if (localStorage.getItem("neverAskConsent") === "true") {
      fetchLocation();
    } else {
      document.getElementById("overlay").classList.add("show");
    }
  }
  function closePopup() {
    document.getElementById("overlay").classList.remove("show");
  }
  function acceptConsent() {
    const neverAsk = document.getElementById("never-ask").checked;
    if (neverAsk) {
      localStorage.setItem("neverAskConsent", "true");
    }
    fetchLocation();
  }

  // --- Fetch Location ---
  function fetchLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(function(position) {
        userLocation = position.coords;
        fetchWeatherByCoords(userLocation.latitude, userLocation.longitude);
        closePopup();
      }, function() {
        document.getElementById("error-message").innerText = "Unable to fetch location.";
        closePopup();
      });
    } else {
      document.getElementById("error-message").innerText = "Geolocation is not supported by this browser.";
      closePopup();
    }
  }
  // --- Fetch Weather by Coordinates ---
  async function fetchWeatherByCoords(lat, lon) {
    try {
      const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${apiKey}&units=${unit}`);
      const data = await response.json();
      document.getElementById("error-message").innerText = "";
      const cityName = `${data.name}, ${data.sys.country}`;
      // Also set the search box to this location
      document.getElementById("city-input").value = cityName;
      fetchWeather(cityName);
    } catch (error) {
      console.error('Error fetching weather by coordinates:', error);
      showNoWifiError();
    }
  }
  // --- Helper: Fetch Precipitation Chance ---
  async function fetchPrecipChance(city) {
    try {
      const response = await fetch(`https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${apiKey}&units=${unit}`);
      const data = await response.json();
      if (data.list && data.list.length > 0) {
        return Math.round(data.list[0].pop * 100);
      } else {
        return 0;
      }
    } catch (error) {
      console.error("Error fetching precipitation chance:", error);
      return 0;
    }
  }
  // --- Determine Precipitation Type from Description ---
  function getPrecipType(description) {
    const desc = description.toLowerCase();
    if (desc.includes("snow")) return "snow";
    if (desc.includes("ice")) return "ice";
    if (desc.includes("wintry")) return "wintry";
    if (desc.includes("rain")) return "rain";
    return "rain";
  }
  // --- Generate Precipitation Graph HTML ---
  function getPrecipGraphHTML(precip, precipType) {
    let color = "";
    if (precipType === "rain") {
      if (precip <= 25) color = "green";
      else if (precip <= 50) color = "lightgreen";
      else if (precip <= 75) color = "yellow";
      else if (precip < 100) color = "orange";
      else color = "crimson";
    } else if (precipType === "snow") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "blue";
      else color = "darkblue";
    } else if (precipType === "ice") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "pink";
      else color = "deeppink";
    } else if (precipType === "wintry") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "purple";
      else color = "indigo";
    } else {
      color = "green"; // default for rain
    }
    // Return a small bar with width proportional to precip percentage
    return `<div style="display:inline-block; width:${precip}%; height:10px; background-color:${color}; margin-left:5px;"></div>`;
  }
  // --- Fetch and Display Weather Info ---
  async function fetchWeather(city) {
    try {
      const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=${unit}`);
      const data = await response.json();
      if (data.cod === "404") {
        document.getElementById("error-message").innerText = "City not found.";
        document.getElementById("weather-result").innerHTML = "";
        document.getElementById("hourly-forecast").innerHTML = "";
        return;
      }
      document.getElementById("error-message").innerText = "";
      addToHistory(`${data.name}, ${data.sys.country}`);
      document.getElementById("current-location").innerText = `Location: ${data.name}, ${data.sys.country}`;
      const precipChance = await fetchPrecipChance(city);
      const precipType = getPrecipType(getWeatherDescription(data.weather[0].description));
      const temp = Math.round(data.main.temp);
      const realFeel = Math.round(data.main.feels_like);
      const description = getWeatherDescription(data.weather[0].description);
      const windSpeed = Math.round(data.wind.speed * 2.237); // m/s to mph
      const windGusts = data.wind.gust ? Math.round(data.wind.gust * 2.237) : 0;
      const weatherHTML = `
        <img class="weather-icon" src="https://openweathermap.org/img/wn/${data.weather[0].icon}.png" alt="weather icon">
        <div class="temp">${temp}°${unit === 'metric' ? 'C' : 'F'}</div>
        <div>${description} <span style="color: #aaa;">| ${precipChance}%</span> ${getPrecipGraphHTML(precipChance, precipType)}</div>
        <div class="real-feel">Real Feel: ${realFeel}°${unit === 'metric' ? 'C' : 'F'}</div>
        <div class="details">
          <div>Humidity: ${data.main.humidity}%</div>
          <div>Wind Speed: ${windSpeed} mph</div>
          <div>Wind Gusts: ${windGusts} mph</div>
        </div>
      `;
      document.getElementById("weather-result").innerHTML = weatherHTML;
      document.getElementById("radar-embed").innerHTML = `
        <iframe src="https://radar.weather.gov/?settings=v1_eyJhZ2VuZGEiOnsiaWQiOm51bGwsImNlbnRlciI6Wy02Ni4yODMsMzguNDIxXSwibG9jYXRpb24iOm51bGwsInpvb20iOjQuMDAwOTE1NjQ1NjM4NzU2fSwiYW5pbWF0aW5nIjpmYWxzZSwiYmFzZSI6InN0YW5kYXJkIiwiYXJ0Y2MiOmZhbHNlLCJjb3VudHkiOmZhbHNlLCJjd2EiOmZhbHNlLCJyZmMiOmZhbHNlLCJzdGF0aW9ucyI6ZmFsc2UsIm1lbnUiOnRydWUsInNob3J0RnVzZWRPbmx5IjpmYWxzZSwib3BhY2l0eSI6eyJhbGVydHMiOjAuOCwibG9jYWwiOjAuNiwibG9jYWxTdGF0aW9ucyI6MC44LCJuYXRpb25hbCI6MC42fX0%3D" width="100%" height="400" style="border: none;"></iframe>
      `;
      fetchHourlyForecast(city);
    } catch (error) {
      console.error('Error fetching weather:', error);
      showNoWifiError();
    }
  }
  // --- Fetch Hourly Forecast ---
  async function fetchHourlyForecast(city) {
    try {
      const response = await fetch(`https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${apiKey}&units=${unit}`);
      const data = await response.json();
      const hourlyHTML = data.list.slice(0, 24).map(hour => {
        const hourTime = new Date(hour.dt * 1000);
        const hourTemp = Math.round(hour.main.temp);
        const hourRealFeel = Math.round(hour.main.feels_like);
        const hourDescription = getWeatherDescription(hour.weather[0].description);
        const hourPrecip = Math.round(hour.pop * 100);
        const precipType = getPrecipType(hourDescription);
        const precipGraph = getPrecipGraphHTML(hourPrecip, precipType);
        const hourTimeFormatted = formatTime(hourTime);
        return `
          <div class="hourly-item">
            <div class="hour-time">${hourTimeFormatted}</div>
            <div class="hour-details">
              <img class="weather-icon" src="https://openweathermap.org/img/wn/${hour.weather[0].icon}.png" alt="icon">
              <span>${hourDescription} <span style="color: #aaa;">| ${hourPrecip}%</span> ${precipGraph}</span>
            </div>
            <div class="hour-temperature">
              <strong>${hourTemp}°${unit === 'metric' ? 'C' : 'F'}</strong><br>
              <span class="real-feel">${hourRealFeel}°${unit === 'metric' ? 'C' : 'F'}</span>
            </div>
          </div>
        `;
      }).join('');
      document.getElementById("hourly-forecast").innerHTML = hourlyHTML;
    } catch (error) {
      console.error('Error fetching hourly forecast:', error);
      showNoWifiError();
    }
  }
  // --- Format Time Helper ---
  function formatTime(date) {
    const hours = date.getHours();
    const minutes = date.getMinutes().toString().padStart(2, '0');
    const ampm = hours >= 12 ? 'PM' : 'AM';
    const formattedHours = hours % 12 || 12;
    return `${formattedHours}:${minutes} ${ampm}`;
  }
  // --- Weather Description Mapping ---
  function getWeatherDescription(description) {
    const mapping = {
      "clear sky": "Clear Sky",
      "few clouds": "Mostly Sunny",
      "scattered clouds": "Mostly Cloudy",
      "broken clouds": "Mostly Cloudy",
      "shower rain": "Scattered Showers",
      "rain": "Heavy Rain",
      "thunderstorm": "Scattered Thunderstorms",
      "snow": "Heavy Snow",
      "mist": "Foggy"
    };
    return mapping[description] || description.charAt(0).toUpperCase() + description.slice(1);
  }
  // --- Get Precipitation Type ---
  function getPrecipType(description) {
    const desc = description.toLowerCase();
    if (desc.includes("snow")) return "snow";
    if (desc.includes("ice")) return "ice";
    if (desc.includes("wintry")) return "wintry";
    if (desc.includes("rain")) return "rain";
    return "rain";
  }
  // --- Generate Precipitation Graph HTML ---
  function getPrecipGraphHTML(precip, precipType) {
    let color = "";
    if (precipType === "rain") {
      if (precip <= 25) color = "green";
      else if (precip <= 50) color = "lightgreen";
      else if (precip <= 75) color = "yellow";
      else if (precip < 100) color = "orange";
      else color = "crimson";
    } else if (precipType === "snow") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "blue";
      else color = "darkblue";
    } else if (precipType === "ice") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "pink";
      else color = "deeppink";
    } else if (precipType === "wintry") {
      if (precip <= 50) color = "white";
      else if (precip < 100) color = "purple";
      else color = "indigo";
    } else {
      color = "green"; // default for rain
    }
    return `<div style="display:inline-block; width:${precip}%; height:10px; background-color:${color}; margin-left:5px;"></div>`;
  }
  // --- Update Weather Unit ---
  function updateWeatherUnit() {
    unit = document.getElementById("unit-dropdown").value;
    const city = document.getElementById("city-input").value;
    if (city) {
      fetchWeather(city);
    } else if (userLocation) {
      fetchWeatherByCoords(userLocation.latitude, userLocation.longitude);
    }
  }
</script>

</body>
</html>
