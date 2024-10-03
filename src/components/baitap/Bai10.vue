<template>
    <div>
      <h1>Đồng hồ: {{ time }}</h1>
    </div>
</template>
  
<script>
  export default {
    name: 'Clock',
    data() {
      return {
        time: '', // Khởi tạo biến time
        interval: null, // Biến để lưu trữ ID của interval
      };
    },
    methods: {
      updateTime() {
        const now = new Date(); // Lấy thời gian hiện tại
        const hours = String(now.getHours()).padStart(2, '0'); // Lấy giờ và thêm 0 nếu cần
        const minutes = String(now.getMinutes()).padStart(2, '0'); // Lấy phút và thêm 0 nếu cần
        const seconds = String(now.getSeconds()).padStart(2, '0'); // Lấy giây và thêm 0 nếu cần
        this.time = `${hours} : ${minutes} : ${seconds}`; // Cập nhật giá trị time
      },
    },
    mounted() {
      this.updateTime(); // Cập nhật thời gian ngay khi component được mount
      this.interval = setInterval(this.updateTime, 1000); // Thiết lập interval để cập nhật thời gian mỗi giây
    },
    beforeUnmount() {
      clearInterval(this.interval); // Dọn dẹp interval khi component bị hủy
    },
  };
</script>
  
<style scoped></style>
  