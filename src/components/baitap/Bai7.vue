<template>
    <div>
      <h1>Enter a title for the tab</h1>
      <input v-model="inputValue" placeholder="Type here to change tab title" />
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise07',
    data() {
      return {
        inputValue: '', // Khởi tạo biến để lưu giá trị từ input
      };
    },
    watch: {
      inputValue(newTitle) {
        document.title = newTitle || 'Default Title'; // Cập nhật tiêu đề tab, nếu input rỗng thì để tiêu đề mặc định
      },
    },
    mounted() {
      document.title = 'Default Title'; // Đặt tiêu đề mặc định khi component được mount
    },
  };
</script>
  
<style></style>
  