<script>
import axios from 'axios';

export default {

  // add code here
  data() {
    return {
      subject: "",
      entry: "",
      mood: "Happy",
      moods: ["Happy", "Sad", "Angry"]
    }
  },

  methods: {
    createPost() {
      const queryParams = new URLSearchParams({ subject: this.subject, entry: this.entry, mood: this.mood })
      axios.get(`http://localhost:3000/addPost?${queryParams}`)
      this.subject = ""
      this.entry = ""
      this.mood = ""
    }
  }
}
</script>

<template>
  <div class="table m-2">
    <h3>Add a New Blog Post</h3>

    Subject: <input type='text' size='30' v-model='subject' required>
    <br>

    Entry: <br>
    <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
    <br>

    Mood:
    <select role="combobox" v-model="mood">
      <option v-for="(mood, idx) in moods" :key="idx" :value="mood">{{ mood }}</option>
    </select>

    <br>

    <br>
    <button @click="createPost">Submit New Post</button>

    <hr> Click <a><router-link to="/ViewPosts/">here</router-link></a> to return to Main Page

  </div>
</template>
