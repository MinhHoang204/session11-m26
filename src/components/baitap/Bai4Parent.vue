<template>
    <div>
      <h1>Parent Component</h1>
      <p>Age: {{ age }}</p>
      <button @click="increaseAge">Increase age</button>
  
      <!-- Truyền giá trị age xuống component con -->
      <Bai4Children :age="age" />
    </div>
</template>
  
<script>
  import Bai4Children from './Bai4Children.vue'; // Import component con
  
  export default {
    name: 'Exercise04Parent',
    components: {
      Exercise03Children, // Đăng ký component con
    },
    data() {
      return {
        age: 1, // Biến lưu trữ giá trị age
      };
    },
    methods: {
      increaseAge() {
        this.age += 1; // Tăng giá trị age lên 1 đơn vị khi nhấn nút
      },
    },
  };
</script>
  
<style></style>
  