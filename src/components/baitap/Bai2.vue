<template>
    <div>
      <h1>Counter: {{ count }}</h1>
      <button @click="incrementCount">Counter</button>
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise02',
    data() {
      return {
        count: 0, // Biến count
      };
    },
    methods: {
      incrementCount() {
        this.count += 1; // Tăng giá trị count lên 1 đơn vị khi nhấn nút
      },
    },
    watch: {
      count() {
        console.log('Dữ liệu đã thay đổi'); // In thông báo khi count thay đổi
      },
    },
  };
</script>
  
<style></style>
  