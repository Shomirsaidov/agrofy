<template>
  <div>
    <TopBar />

    <div class="px-40 p-3 rounded-xl">
      <div class="flex p-3 space-x-6">
        <!-- Left Column: Input fields -->
        <div>
          <h3 class="text-2xl font-bold text-my text-start my-6">Add your field</h3>
          <div class="myGreen2 rounded-xl p-3 space-y-3">
            <input
              type="text"
              autofocus
              placeholder="Add a title"
              v-model="fieldTitle"
              class="focus:shadow-md border p-4 outline-none rounded-xl w-full"
            />
            <div class="flex space-x-3">
              <input
                type="text"
                placeholder="Soil type"
                v-model="soilType"
                class="focus:shadow-md border p-4 outline-none rounded-xl"
              />
              <input
                type="number"
                placeholder="Field area"
                v-model="fieldArea"
                class="focus:shadow-md border p-4 outline-none rounded-xl"
              />
            </div>
            <textarea
              type="text"
              placeholder="Type a description"
              v-model="description"
              class="focus:shadow-md border w-full p-4 outline-none rounded-xl"
            ></textarea>

            <!-- Uploadcare Widget for Multiple Image Uploads -->
            <input
              type="hidden"
              role="uploadcare-uploader"
              data-crop="free"
              data-multiple="true" 
              data-public-key="a0c09e05ae42395c7d5c"
              id="file-uploader"
            />

            <!-- Display uploaded image URLs -->
            <div v-if="uploadedImageUrls.length > 0" class="mt-4 p-4 bg-gray-100 rounded-lg">
              <p class="text-sm text-gray-700">Uploaded Image URLs:</p>
              <ul class="list-disc ml-5">
                <li v-for="url in uploadedImageUrls" :key="url" class="text-blue-500 underline">
                  <a :href="url" target="_blank">{{ url }}</a>
                </li>
              </ul>
            </div>

            <button @click="sendData" class="p-4 w-full myGreen4 text-white font-bold rounded-lg my-8">
              Continue
            </button>
          </div>
        </div>

        <!-- Right Column: Map container -->
        <div class="w-full">
          <h3 class="text-xl font-bold text-my text-start my-6">Select your area</h3>
          <div id="map" class="w-full h-96 rounded-xl"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TopBar from '@/components/TopBar.vue';
import L from 'leaflet'; // Import Leaflet library

import axios from 'axios';

// Import Uploadcare if installed via npm
import uploadcare from 'uploadcare-widget';

export default {
  components: {
    TopBar,
  },
  data() {
    return {
      map: null,                 // Store the Leaflet map instance
      marker: null,
      fieldCords: null,          // Store the Leaflet marker instance
      uploadedImageUrls: [],     // Array to store URLs of multiple uploaded images
    };
  },
  mounted() {
    // Initialize the map once the component is mounted
    this.initMap();
    this.initUploadcare();
  },
  methods: {
    async sendData() {
          // Construct data object to be sent with the POST request
          const postData = {
            title: this.fieldTitle,
            description: this.description,
            area: `${this.fieldArea}`,
            longtitude: `${this.fieldCords.lng}`,
            latitude	: `${this.fieldCords.lat}`,
            soil_type: this.soilType,
            images: this.uploadedImageUrls[0],
          

          };
  
          console.log('Coords:', postData.longtitude); // Debugging log
          console.log('Images:', postData.images); // Debugging log
  

          try {
            const response = await axios({
              method: 'post', // Change method as needed
              url: 'https://agrofy-app-gsghy.ondigitalocean.app/api/v1/my-fields/',
              headers: {
                Authorization: `Token ${localStorage.nasa}`, // Ensure the token is formatted correctly
                'Content-Type': 'application/json' // Specify content type
              },
              data: postData // Use `data` to pass the request body, not `body`
            });

            console.log(response.data);
            alert('Field added successfully!');
          } catch (error) {
            if (error.response) {
              // The request was made and the server responded with a status code
              console.error('Error response data:', error.response.data);
              console.error('Error response status:', error.response.status);
              console.error('Error response headers:', error.response.headers);
              alert(`Failed to add field. Server responded with: ${error.response.status} - ${error.response.data.message || error.response.data}`);
            } else if (error.request) {
              // The request was made but no response was received
              console.error('Error request:', error.request);
              alert('Failed to add field. No response received from the server.');
            } else {
              // Something happened in setting up the request that triggered an Error
              console.error('Error message:', error.message);
              alert('Failed to add field. Error: ' + error.message);
            }
          }
          
          // Handle success (e.g., show a notification, redirect, etc.)
       
    },
    initMap() {
      // Create the map and set its initial view
      this.map = L.map('map').setView([51.505, -0.09], 13); // Replace with your desired coordinates

      // Add a tile layer (OpenStreetMap)
      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 19,
        attribution: '&copy; OpenStreetMap contributors',
      }).addTo(this.map);

      // Listen for map click events
      this.map.on('click', this.onMapClick);
    },
    onMapClick(event) {
      // Extract latitude and longitude from the click event
      const { lat, lng } = event.latlng;

      // If a marker already exists, update its position
      if (this.marker) {
        this.marker.setLatLng([lat, lng]);
      } else {
        // Otherwise, create a new marker at the clicked position
        this.marker = L.marker([lat, lng]).addTo(this.map);
      }

      // Optionally, show a popup with coordinates on the marker
      this.marker.bindPopup(`Latitude: ${lat.toFixed(5)}, Longitude: ${lng.toFixed(5)}`).openPopup();


      // Save the coordinates or perform any desired action
      console.log('Selected coordinates:', { lat, lng });
      this.fieldCords = { lat, lng };
    },
    initUploadcare() {
      // Initialize the Uploadcare widget and handle events
      const widget = uploadcare.Widget('[role=uploadcare-uploader]');

      // Listen for when multiple files have been uploaded
      widget.onUploadComplete((fileGroupInfo) => {
        // fileGroupInfo contains information about the uploaded files
        if (fileGroupInfo.files) {
          // Extract URLs of all uploaded files and store them in uploadedImageUrls
          this.uploadedImageUrls = fileGroupInfo.files.map(file => file.cdnUrl);
        } else {
          // If single file, use the single URL (fallback)
          this.uploadedImageUrls = [fileGroupInfo.cdnUrl];
        }

        console.log('Uploaded file URLs:', this.uploadedImageUrls);
      });
    },
  },
};
</script>

<style scoped>
/* Add any custom styles for the component here if needed */
</style>
