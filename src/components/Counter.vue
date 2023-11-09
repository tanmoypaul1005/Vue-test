<!-- src/components/ApiData.vue -->
<template>
  <div>
  <!-- <div>
    <div v-if="loading">Loading data...</div>
    <div v-else>
      <h1>Data from API:</h1>
      <pre>{{ apiData.title }}</pre>
    </div>
  </div> -->
  
    <div v-if="loading">Loading data...</div>
    <div v-else>
      <ul>
        <li v-for="item in apiData" :key="item.id">{{ item.title }}</li>
      </ul>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  data() {
    return {
      apiData: null,
      loading: true
    };
  },

  async mounted() {
    try {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/todos"
      ); // Replace with your API endpoint
      console.log("response", response);
      if (response.ok) {
        const data = await response.json();
        console.log("response", data);
        this.apiData = data;
        this.loading = false;
      } else {
        console.error("API request failed:", response.status);
        this.loading = false;
      }
    } catch (error) {
      console.error("API request failed:", error);
      this.loading = false;
    }
  }
};
</script>
