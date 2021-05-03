<template>
  <div class="home">
    <div v-for="note in notes" :key="note.id">
      <h2>{{ note.title }}</h2>
      <p>{{ note.content }}</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      notes: [],
    };
  },
  async mounted() {
    try {
      const response = await axios.get("http://localhost:3000/notes");
      this.notes = response.data;
    } catch (error) {
      console.error(error);
    }
  },
};
</script>
