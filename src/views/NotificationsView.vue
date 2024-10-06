<template>

    <TopBar/>

    <div class="notifications-container p-8 bg-gray-100 min-h-screen">
      <h1 class="text-3xl font-bold text-gray-800 mb-6 min-w-1/2 text-my">Weather Adversity Notifications</h1>
      <div v-for="(notification, index) in notifications" :key="index" class="notification-card p-6 mb-4 bg-white rounded-lg shadow-lg border-l-4 border-blue-500 hover:shadow-2xl transition-all">
        <h2 class="text-xl font-semibold text-blue-600 mb-2">{{ notification.title }}</h2>
        <p class="text-gray-700 mb-4">{{ notification.description }}</p>
        <p class="text-sm text-gray-500"><strong>Date:</strong> {{ notification.date }}</p>
      </div>
    </div>
  </template>
  
  <script>


    import TopBar from '@/components/TopBar.vue'


  export default {
    name: 'Notif',
    components: {
        TopBar
    },
    data() {    
      return {
        notifications: [
          {
            title: "Severe Drought Alert: Water Your Crops Wisely!",
            description: "A prolonged drought has been detected in your region. Soil moisture levels are critically low, which may impact crop growth. Consider implementing water conservation strategies and monitor irrigation schedules closely to prevent crop stress.",
            date: "March 15, 2024"
          },
          {
            title: "Heavy Rainfall Expected: Risk of Crop Damage and Soil Erosion",
            description: "Forecasts indicate significant rainfall over the next 48 hours. This can cause soil erosion and waterlogging. Ensure proper drainage systems are in place and consider protective measures to minimize crop damage.",
            date: "April 10, 2024"
          },
          {
            title: "Frost Warning: Protect Your Crops from Cold Damage!",
            description: "An overnight frost is expected in your area. Low temperatures may damage sensitive crops. Consider using frost blankets or adjusting greenhouse conditions to maintain optimal temperatures.",
            date: "January 22, 2024"
          },
          {
            title: "High Winds Advisory: Risk of Crop Lodging",
            description: "Strong winds are forecasted for the next few days, increasing the risk of crop lodging and physical damage. Reinforce crop supports and remove any loose debris to minimize harm to plants.",
            date: "May 3, 2024"
          },
          {
            title: "Heatwave Alert: Elevated Temperatures Could Impact Crop Yield",
            description: "A heatwave is predicted for your area, with temperatures exceeding normal ranges. Ensure adequate irrigation and consider shading sensitive crops to reduce heat stress and maintain productivity.",
            date: "July 20, 2024"
          },
          {
            title: "Hailstorm Risk: Prepare for Potential Crop Damage!",
            description: "Hailstorms are likely in the upcoming weather pattern. Hail can cause significant physical damage to plants. Protect your crops by using coverings or temporary shelters where feasible.",
            date: "August 12, 2024"
          }
        ]
      };
    }
  }
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
  