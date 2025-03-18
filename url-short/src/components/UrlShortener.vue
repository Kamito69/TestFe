<template>
    <div class="container">
      <h2>Rút gọn URL</h2>
      
      <input v-model="originalUrl" placeholder="Nhập URL gốc" />
      <button @click="shortenUrl">Rút gọn</button>
  
      <h3>Danh sách URL rút gọn</h3>
      <ul v-if="shortenedUrls.length">
        <li v-for="url in shortenedUrls" :key="url.short_code">
          <a :href="url.original_url" target="_blank">{{ `http://short-link/${url.short_code}` }}</a>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        originalUrl: "",
        shortenedUrls: [] // Lưu danh sách toàn bộ URL từ DB
      };
    },
    methods: {
      async shortenUrl() {
        try {
          const response = await axios.post("http://127.0.0.1:8000/api/shorten", {
            original_url: this.originalUrl,
          });
  
          // Gọi API để cập nhật danh sách mới từ DB
          this.fetchUrls();
  
          // Xóa ô nhập sau khi tạo thành công
          this.originalUrl = "";
        } catch (error) {
          console.error("Lỗi:", error);
        }
      },
  
      async fetchUrls() {
        try {
          const response = await axios.get("http://127.0.0.1:8000/api/urls");
          this.shortenedUrls = response.data;
        } catch (error) {
          console.error("Lỗi:", error);
        }
      }
    },
    mounted() {
      this.fetchUrls(); // Lấy danh sách URL ngay khi component được render
    }
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
    width: 300px;
  }
  button {
    padding: 10px;
    cursor: pointer;
  }
  ul {
    list-style: none;
    padding: 0;
  }
  li {
    margin-top: 10px;
  }
  </style>
  