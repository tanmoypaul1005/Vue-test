<template>
  <form @submit="submitForm">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="formData.name" />

    <label for="description">Description:</label>
    <textarea id="description" v-model="formData.description"></textarea>

    <button type="submit">Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        description: '',
      },
    };
  },
  methods: {
  async submitForm() {
    try {
      const response = await axios.post('https://api.example.com/data', this.formData);
      console.log('Data saved:', response.data);
    } catch (error) {
      console.error('Failed to save data:', error);
    }
  },
},

};
</script>
