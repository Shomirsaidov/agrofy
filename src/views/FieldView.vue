<template>
    <TopBar />
    <div class="px-40 pt-16 pb-2 flex justify-center">
      <div>
        <div>
          <div class="flex items-stretch space-x-3">
            <div class="" style="position: relative;">
              <img src="../assets/pole1.png" style="height: 400px;" alt="" />
              <button
                class="flex items-center bg-white p-2 rounded-xl space-x-3"
                style="position: absolute; top: 20px; left: 20px;"
              >
                <img src="../assets/location.svg" alt="" />
                <span>Fotehobod, Uzbekistan</span>
              </button>
            </div>
            <div>
              <div class="flex space-x-3 mb-2">
                <img style="height: 200px" src="../assets/uzbekistan_polya 1.png" alt="" />
                <img style="height: 200px" src="../assets/uzbekistan_polya 1.png" alt="" />
              </div>
              <div class="flex space-x-3">
                <img style="height: 200px" src="../assets/uzbekistan_polya 1.png" alt="" />
                <img style="height: 200px" src="../assets/uzbekistan_polya 1.png" alt="" />
              </div>
            </div>
          </div>
          <div class="my-8">
            <div class="scale-container">
              <div class="scale"></div>
              <div class="scale-container-empty" :style="scaleStyle">
                <div class="scale" :style="scaleStyle"></div>
              </div>
            </div>
  
            <p class="mt-4 text-2xl text-my font-bold text-end">
              Overall well-being score: {{ 100 - scale_value }} %
            </p>
          </div>
        </div>
  
        <div class="flex my-16 space-x-20">
          <div class="space-y-8">
            <h2 class="font-bold text-3xl text-start">
              Lorem ipsum dolor sit, amet consectetur adipisicing.
            </h2>
            <p class="text-start text-xl">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
            </p>
            <div class="flex space-x-16">
              <div class="flex space-x-2 items-center">
                <img src="../assets/area.svg" alt="" />
                <span class="font-bold">20g</span>
              </div>
              <div class="flex space-x-2 items-center">
                <img src="../assets/soil.svg" alt="" />
                <span class="font-bold">Clay</span>
              </div>
            </div>
          </div>
          <div class="border-2 rounded-lg shadow-xl p-10 pe-16 space-y-8">
            <h2 class="text-xl text-start font-bold">Field Health</h2>
            <div class="space-y-8">
              <div class="flex space-x-16">
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop-half.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop-half.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop-half.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
              </div>
              <div class="flex space-x-16">
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
                <div class="flex space-x-2 items-center">
                  <img src="../assets/drop.svg" alt="" />
                  <span class="font-bold">70%</span>
                </div>
              </div>
            </div>
            <button @click="$router.push('/add-seed')" class="p-4 w-full myGreen4 text-white font-bold rounded-lg">Select a seed</button>
            <div>Choose the type of your seed</div>
          </div>
        </div>
      </div>
    </div>
  
    <div class="my px-40">
      <h2 class="font-bold text-3xl text-start">
        Be ready for future precipitations and soil moisture 
      </h2>
      <h5 class="text-start mb-8">*NASA Satelite Sources</h5>
      <div class="flex space-x-8">
        <canvas id="precipitationChart" width="400" class="my-8" height="500"></canvas>
        <canvas id="soilMoistureChart" width="400" class="my-8" height="500"></canvas> <!-- New Soil Moisture Chart -->
      </div>
    </div>
  </template>
  
  <script>
  import TopBar from '@/components/TopBar.vue';
  import axios from 'axios';
  import { Chart, registerables } from 'chart.js';
  
  Chart.register(...registerables);
  
  export default {
    data: () => ({
      scale_value: 10,
      precipitationData: [],
      soilMoistureData: [], // New data property for soil moisture
      labels: [],
      latitude: 51.52374, // Latitude of Fotehobod, Uzbekistan
      longitude: -0.11204, // Longitude of Fotehobod, Uzbekistan
    }),
    components: {
      TopBar,
    },
    async mounted() {
      this.fetchPrecipitationForecast();
    },
    methods: {
      async fetchPrecipitationForecast() {
        try {
          const response = await axios.get('https://api.open-meteo.com/v1/forecast', {
            params: {
              latitude: this.latitude,
              longitude: this.longitude,
              hourly: 'precipitation', // Correct parameter for hourly precipitation
              timezone: 'auto', // Adjust to local timezone
            },
          });
  
          // Check the API response structure
          if (response.data && response.data.hourly) {
            this.precipitationData = response.data.hourly.precipitation; // This should get the hourly precipitation data
            this.labels = response.data.hourly.time; // Get the hourly time labels
            this.renderPrecipitationChart(); // Render the chart with the new data
            this.renderSoilMoistureChart(); // Render the soil moisture chart as well
          } else {
            console.error('Invalid data format:', response.data);
          }
        } catch (error) {
          console.error('Error fetching precipitation forecast:', error);
        }
      },
      renderPrecipitationChart() {
        const ctx = document.getElementById('precipitationChart').getContext('2d');
        new Chart(ctx, {
          type: 'line',
          data: {
            labels: this.labels.map((time) => new Date(time).toLocaleString()), // Format time for labels
            datasets: [
              {
                label: 'Hourly Precipitation Forecast (mm)',
                data: this.precipitationData,
                borderColor: 'rgba(75, 192, 192, 1)',
                backgroundColor: 'rgba(75, 192, 192, 0.2)',
                borderWidth: 2,
                fill: true,
              },
            ],
          },
          options: {
            responsive: false, // Set to false to respect hardcoded dimensions
            scales: {
              y: {
                beginAtZero: true,
                title: {
                  display: true,
                  text: 'Precipitation (mm)',
                },
              },
              x: {
                title: {
                  display: true,
                  text: 'Time',
                },
              },
            },
          },
        });
      },
      renderSoilMoistureChart() {
        // Assuming you have soil moisture data; you can adjust the data fetching logic accordingly.
        this.soilMoistureData = this.precipitationData.map(p => Math.min(p + 30, 100)); // Dummy calculation for soil moisture (could be from API)
  
        const ctx = document.getElementById('soilMoistureChart').getContext('2d');
        new Chart(ctx, {
          type: 'bar', // Change type to 'bar' or any other type that suits your data
          data: {
            labels: this.labels.map((time) => new Date(time).toLocaleString()), // Format time for labels
            datasets: [
              {
                label: 'Soil Moisture Level (%)',
                data: this.soilMoistureData,
                backgroundColor: 'rgba(153, 102, 255, 0.6)',
                borderColor: 'rgba(153, 102, 255, 1)',
                borderWidth: 1,
              },
            ],
          },
          options: {
            responsive: false,
            scales: {
              y: {
                beginAtZero: true,
                title: {
                  display: true,
                  text: 'Soil Moisture (%)',
                },
              },
              x: {
                title: {
                  display: true,
                  text: 'Time',
                },
              },
            },
          },
        });
      },
    },
  };
  </script>
  
  <style>
  .scale-container {
    width: 100%; /* Width of the scale */
    height: 20px; /* Height of the scale */
    background: linear-gradient(90deg, indianred, lime); /* Color of the empty part */
    position: relative;
    border-radius: 50px;
  }
  
  .scale {
    position: absolute;
    bottom: 0; /* Start filling from the bottom */
    width: 100%; /* Fill the width of the container */
    transition: height 0.3s; /* Smooth transition when height changes */
  }
  
  .scale-container-empty {
    background: #dcdcdc;
    border: 2px black;
    width: 30%; /* Width of the scale */
    height: 20px; /* Height of the scale */
    position: absolute;
    right: 0;
    border-radius: 50px;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
  }
  </style>
  