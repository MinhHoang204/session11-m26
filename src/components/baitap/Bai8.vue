<template>
    <div>
      <h1>Chiều rộng cửa sổ: {{ windowWidth }}px</h1>
    </div>
</template>
  
<script>
  export default {
    name: 'GetWidthWindow',
    data() {
      return {
        windowWidth: window.innerWidth, // Khởi tạo giá trị chiều rộng ban đầu
      };
    },
    methods: {
      updateWidth() {
        this.windowWidth = window.innerWidth; // Cập nhật giá trị khi resize
      },
    },
    mounted() {
      window.addEventListener('resize', this.updateWidth); // Lắng nghe sự kiện resize khi component được mount
    },
    beforeUnmount() {
      window.removeEventListener('resize', this.updateWidth); // Ngừng lắng nghe sự kiện resize khi component bị hủy
    },
  };
</script>
  
<style></style>
  