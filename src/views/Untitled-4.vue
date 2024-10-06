<template>
    <div>
      <TopBar />
      <div class="notifications-container p-8 bg-gray-100 min-h-screen mt-8">
        <h1 class="text-3xl font-bold text-gray-800 mb-6 min-w-3/4 text-my">Weather Adversity Notifications</h1>
        <div v-if="loading" class="text-center text-gray-500">Loading notifications...</div>
        <div v-if="!loading && notifications.length === 0" class="text-center text-gray-500">No weather alerts at the moment.</div>
        <div v-for="(notification, index) in notifications" :key="index" class="notification-card p-6 mb-4 bg-white rounded-lg shadow-lg border-l-4 border-blue-500 hover:shadow-2xl transition-all">
          <h2 class="text-xl font-semibold text-blue-600 mb-2">{{ notification.title }}</h2>
          <p class="text-gray-700 mb-4">{{ notification.description }}</p>
          <p class="text-sm text-gray-500"><strong>Date:</strong> {{ new Date(notification.date).toLocaleDateString() }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import TopBar from '@/components/TopBar.vue';
  
  export default {
    name: 'Notif',
    components: {
      TopBar,
    },
    data() {
      return {
        notifications: [],  // Store notifications from the API
        loading: true,      // Display a loading state
      };
    },
    mounted() {
      this.fetchWeatherAlerts();
    },
    methods: {
      async fetchWeatherAlerts() {
        try {
          // Replace with your OpenWeatherMap API key
          const API_KEY = '7c0d8adac6a5c49d486cb4b12268c79a';
          // Example coordinates (latitude and longitude) - modify these as needed
          const LAT = '35.6895';
          const LON = '139.6917';
          const url = `https://api.openweathermap.org/data/3.0/onecall?lat=${LAT}&lon=${LON}&appid=${API_KEY}`;
  
          // Fetch the alerts data from OpenWeatherMap
          const response = await axios.get(url);
  
          if (response.data && response.data.alerts) {
            // Format the data into our notification structure
            this.notifications = response.data.alerts.map((alert) => ({
              title: alert.event,
              description: alert.description,
              date: alert.start * 1000, // Convert Unix timestamp to milliseconds
            }));
          }
        } catch (error) {
          console.error('Failed to fetch weather alerts:', error);
        } finally {
          this.loading = false; // Stop loading state
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .notifications-container {
    /* Center the content vertically and horizontally */
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .notification-card {
    /* Set a maximum width for each card */
    max-width: 600px;
    width: 100%;
  }
  </style>
  