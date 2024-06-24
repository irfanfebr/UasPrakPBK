<template>
    <q-page class="weather-page">
      <q-header elevated>
        <q-toolbar>
          <q-toolbar-title class="title">Weather Detector</q-toolbar-title>
          <q-space />
          <q-btn-dropdown flat label="TUGAS IRFAN" no-caps class="task-dropdown">
            <q-list>
              <q-item clickable v-ripple to="/Tugas1">
                <q-item-section>  
                  <q-item-label>Tugas 1</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas2">
                <q-item-section>
                  <q-item-label>Tugas 2</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas3">
                <q-item-section>
                  <q-item-label>Tugas 3</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas4">
                <q-item-section>
                  <q-item-label>Tugas 4</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas5">
                <q-item-section>
                  <q-item-label>Tugas 5</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas6">
                <q-item-section>
                  <q-item-label>Tugas 6</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable v-ripple to="/Tugas7">
                <q-item-section>
                  <q-item-label>Tugas 7</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-btn-dropdown>
        </q-toolbar>
      </q-header>
  
      <q-card class="weather-card" flat bordered>
        <q-card-section>
          <h2 class="card-title">TODAY'S WEATHER</h2>
          <div class="search-bar">
            <input
              type="text"
              v-model="city"
              placeholder="Enter City Name"
              @keyup.enter="fetchWeather"
              class="city-input"
            />
            <button @click="fetchWeather" class="search-button">Search</button>
          </div>
          <div v-if="weather.main" class="weather-info">
            <h2>{{ city }}</h2>
            <div :class="weatherIcon" class="weather-icon"></div>
            <div class="description">{{ weatherDescription }}</div>
            <div class="temperature">{{ temperature }}°C</div>
          </div>
          <div v-else class="no-data">No weather data available.</div>
        </q-card-section>
      </q-card>
    </q-page>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        city: 'Jakarta',
        weather: {},
        temperature: null,
      };
    },
    computed: {
      weatherIcon() {
        switch (this.weather.main) {
          case 'Clear': return 'icon-sunny';
          case 'Clouds': return 'icon-cloudy';
          case 'Rain': return 'icon-rainy';
          case 'Snow': return 'icon-snowy';
          case 'Thunderstorm': return 'icon-thunderstorm';
          case 'Drizzle': return 'icon-drizzle';
          default: return 'icon-default';
        }
      },
      weatherDescription() {
        return this.weather.description ? this.weather.description.charAt(0).toUpperCase() + this.weather.description.slice(1) : '';
      }
    },
    methods: {
      async fetchWeather() {
        if (!this.city) return;
        const API_KEY = '4d1db2666da951482ad444c5f52dc755';
        try {
          const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${API_KEY}&units=metric`);
          this.weather = response.data.weather[0];
          this.temperature = response.data.main.temp;
        } catch (error) {
          console.error("Error fetching weather data:", error);
          alert("City not found or network error.");
        }
      }
    },
    mounted() {
      this.fetchWeather();
    }
  };
  </script>
  
  <style scoped>
  /* General Styles */
  .weather-page {
    background: #1e272e;
    color: #fff;
    min-height: 100vh;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .q-header {
    background: #0a3d62;
  }
  
  .title {
    font-size: 1.8em;
    font-weight: bold;
    color: #fff;
  }
  
  .task-dropdown .q-list {
    background-color: #0a3d62;
    color: #fff;
  }
  
  .task-dropdown .q-item {
    padding: 12px;
    border-bottom: 1px solid #0a3d62;
  }
  
  .task-dropdown .q-item:hover {
    background-color: #1e3799;
  }
  
  .task-dropdown .q-item-label {
    font-size: 1.2em;
    font-weight: bold;
    color: #fff;
  }
  
  .weather-card {
    background: #485460;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    width: 90%;
    max-width: 800px;
    margin-top: 20px;
    padding: 20px;
  }
  
  .card-title {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 20px;
    text-align: center;
  }
  
  .search-bar {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .city-input {
    padding: 10px;
    border: none;
    border-radius: 8px 0 0 8px;
    width: 60%;
    font-size: 16px;
  }
  
  .search-button {
    padding: 10px 20px;
    border: none;
    border-radius: 0 8px 8px 0;
    background-color: #34ace0;
    color: white;
    cursor: pointer;
  }
  
  .search-button:hover {
    background-color: #227093;
  }
  
  .weather-info {
    background: #ffb142;
    padding: 20px;
    border-radius: 12px;
    color: #2c2c54;
    text-align: center;
  }
  
  .weather-icon {
    margin: 20px 0;
    font-size: 80px;
  }
  
  .icon-sunny::before {
    content: "☀️";
    animation: spin 5s linear infinite;
    font-size: 5rem;
  }
  
  .icon-cloudy::before {
    content: "☁️";
    font-size: 5rem;
    animation: drift 4s ease-in-out infinite;
  }
  
  .icon-rainy::before {
    content: "🌧️";
    font-size: 5rem;
    animation: rain 1s linear infinite;
  }
  
  .icon-snowy::before {
    content: "❄️";
    font-size: 5rem;
    animation: snow 1.5s linear infinite;
  }
  
  .icon-thunderstorm::before {
    content: "🌩️";
    font-size: 5rem;
    animation: flash 0.6s linear infinite;
  }
  
  .icon-drizzle::before {
    content: "🌦️";
    font-size: 5rem;
    animation: drizzle 1.2s linear infinite;
  }
  
  .icon-default::before {
    content: "🌥️";
    font-size: 5rem;
  }
  
  .description {
    font-size: 20px;
    margin: 10px 0;
  }
  
  .temperature {
    font-size: 28px;
    font-weight: bold;
  }
  
  .no-data {
    font-size: 22px;
    color: #777;
    margin-top: 30px;
  }
  
  @keyframes spin {
    to {
      transform: rotate(360deg);
    }
  }
  
  @keyframes drift {
    0%, 100% {
      transform: translateX(0);
    }
    50% {
      transform: translateX(10px);
    }
  }
  
  @keyframes rain {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(10px);
    }
  }
  
  @keyframes snow {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(5px);
    }
  }
  
  @keyframes flash {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.5;
    }
  }
  
  @keyframes drizzle {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(7px);
    }
  }
  </style>
  