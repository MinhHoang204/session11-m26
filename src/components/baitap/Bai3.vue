<template>
    <div>
      <h1>Age: {{ age }}</h1>
      <button @click="randomizeAge">Random</button>
      
      <h2>Company: {{ selectedCompany }}</h2>
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise03',
    data() {
      return {
        age: 1, // Khởi tạo biến age với giá trị mặc định là 1
        companies: ['Rikkei Academy', 'Rikkei Education', 'Rikkei Fukuoka'], // Mảng các công ty
        selectedCompany: 'Rikkei Academy', // Hiển thị công ty mặc định
      };
    },
    methods: {
      randomizeAge() {
        // Cập nhật age ngẫu nhiên trong khoảng từ 1 đến 10
        this.age = Math.floor(Math.random() * 10) + 1;
      },
    },
    watch: {
      age(newAge) {
        // Cập nhật tên công ty theo giá trị age
        const index = (newAge - 1) % this.companies.length; // Lấy index tương ứng với age
        this.selectedCompany = this.companies[index]; // Cập nhật công ty tương ứng
      },
    },
  };
</script>
  
<style></style>
  