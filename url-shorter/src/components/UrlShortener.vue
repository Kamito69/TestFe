<template>
    <div class="container">
      <h2>Rút gọn URL</h2>
      <input v-model="originalUrl" placeholder="Nhập URL gốc" />
      <button @click="shortenUrl">Rút gọn</button>
      <p v-if="shortenedUrl">
        URL rút gọn: <a :href="shortenedUrl" target="_blank">{{ shortenedUrl }}</a>
      </p>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        originalUrl: "",
        shortenedUrl: "",
      };
    },
    methods: {
      async shortenUrl() {
        try {
          const response = await axios.post("http://127.0.0.1:8000/shorten", {
            original_url: this.originalUrl,
          });
          this.shortenedUrl = response.data.shortened_url;
        } catch (error) {
          console.error("Lỗi:", error);
        }
      },
    },
  };
  </script>
  
  <style>
  .container {
    text-align: center;
    margin-top: 50px;
  }
  input {
    padding: 10px;
    margin-right: 10px;
  }
  button {
    padding: 10px;
    cursor: pointer;
  }
  </style>
  