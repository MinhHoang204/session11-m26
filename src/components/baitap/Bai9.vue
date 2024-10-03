<template>
    <div>
      <h1>Counter: {{ count }}</h1>
    </div>
</template>
  
<script>
  export default {
    name: 'Counter',
    data() {
      return {
        count: 0, // Khởi tạo biến count với giá trị 0
      };
    },
    methods: {
      incrementCount() {
        this.count += 1; // Tăng giá trị count lên 1
      },
    },
    mounted() {
      // Thiết lập interval để tăng count mỗi giây
      this.interval = setInterval(this.incrementCount, 1000);
    },
    beforeUnmount() {
      // Dọn dẹp interval khi component bị hủy
      clearInterval(this.interval);
    },
  };
</script>
  
<style></style>
  