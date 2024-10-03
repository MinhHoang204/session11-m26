<template>
    <div class="delete-modal">
      <p>Bạn có chắc chắn muốn xóa thông tin này không?</p>
      <button @click="$emit('confirm')">Xóa</button>
      <button @click="$emit('cancel')">Hủy</button>
    </div>
</template>
  