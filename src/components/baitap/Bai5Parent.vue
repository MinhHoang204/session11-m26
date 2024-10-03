<template>
    <div>
      <h1>Parent Component</h1>
      <button @click="toggleChild">Toggle</button>
      
      <!-- Hiển thị component con dựa vào biến showChild -->
      <Bai5Children v-if="showChild" />
    </div>
</template>
  
<script>
  import Bai5Children from './Bai5Children.vue'; // Import component con
  
  export default {
    name: 'Exercise05Parent',
    components: {
      Exercise05Children, // Đăng ký component con
    },
    data() {
      return {
        showChild: true, // Biến để hiển thị / ẩn component con
      };
    },
    methods: {
      toggleChild() {
        this.showChild = !this.showChild; // Thay đổi trạng thái hiển thị / ẩn component con
      },
    },
  };
</script>
  
<style></style>
  