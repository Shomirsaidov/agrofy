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
                class="focus:shadow-md border p-4 outline-none rounded-xl w-full"
              />
              <div class="flex space-x-3">
                <input
                  type="text"
                  placeholder="Soil type"
                  class="focus:shadow-md border p-4 outline-none rounded-xl"
                />
                <input
                  type="text"
                  placeholder="Field area"
                  class="focus:shadow-md border p-4 outline-none rounded-xl"
                />
              </div>
              <textarea
                type="text"
                placeholder="Type a description"
                class="focus:shadow-md border w-full p-4 outline-none rounded-xl"
              ></textarea>
  
              <!-- Uploadcare Widget for Multiple Image Uploads -->
              <input
                role="uploadcare-uploader"
                type="hidden"
                data-crop="free"
                data-multiple="true"
                data-public-key="a0c09e05ae42395c7d5c" 
                @change="handleUploadComplete"
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
  
              <button class="p-4 w-full myGreen4 text-white font-bold rounded-lg my-8">
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
    },
    methods: {
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
      handleUploadComplete(event) {
        // Handle the upload completion directly from the Uploadcare widget's change event
        const fileGroupInfo = event.detail;
        if (fileGroupInfo && fileGroupInfo.files) {
          // Extract URLs of all uploaded files and store them in `uploadedImageUrls`
          this.uploadedImageUrls = fileGroupInfo.files.map(file => file.cdnUrl);
        } else if (fileGroupInfo && fileGroupInfo.cdnUrl) {
          // If single file, use the single URL (fallback)
          this.uploadedImageUrls = [fileGroupInfo.cdnUrl];
        }
  
        console.log('Uploaded file URLs:', this.uploadedImageUrls);
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add any custom styles for the component here if needed */
  </style>
  