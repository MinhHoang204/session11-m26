<template>
    <div>
      <h1>Count: {{ count }}</h1>
      <button @click="incrementCount">Increment</button>
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise06',
    data() {
      return {
        count: 0, // Khởi tạo biến count với giá trị mặc định là 0
      };
    },
    methods: {
      incrementCount() {
        this.count += 1; // Tăng giá trị của count lên 1 khi nhấn nút
      },
    },
    watch: {
      count(newCount) {
        document.title = `Count: ${newCount}`; // Cập nhật tiêu đề của tab trình duyệt khi count thay đổi
      },
    },
    mounted() {
      document.title = `Count: ${this.count}`; // Thiết lập tiêu đề ban đầu khi component được mount
    },
  };
</script>
  
<style></style>