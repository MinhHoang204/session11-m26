<template>
    <div class="form-modal">
      <h2>{{ record ? 'Cập nhật thông tin' : 'Thêm thông tin mượn sách' }}</h2>
      <input v-model="formData.bookTitle" placeholder="Tên sách" />
      <input v-model="formData.borrowerName" placeholder="Tên người mượn" />
      <input type="date" v-model="formData.borrowDate" />
      <input type="date" v-model="formData.returnDate" />
      <button @click="submitForm">{{ record ? 'Cập nhật' : 'Thêm' }}</button>
      <button @click="$emit('close')">Đóng</button>
    </div>
</template>
  
<script>
  export default {
    props: ['record'],
    data() {
      return {
        formData: {
          bookTitle: this.record ? this.record.bookTitle : '',
          borrowerName: this.record ? this.record.borrowerName : '',
          borrowDate: this.record ? this.record.borrowDate : '',
          returnDate: this.record ? this.record.returnDate : '',
          status: this.record ? this.record.status : 'Chưa trả'
        }
      };
    },
    methods: {
      submitForm() {
        // Validate data
        if (!this.formData.bookTitle || !this.formData.borrowerName || !this.formData.borrowDate || !this.formData.returnDate) {
          alert('Please fill all fields');
          return;
        }
        const today = new Date().toISOString().split('T')[0];
        if (this.formData.borrowDate < today || this.formData.returnDate < today) {
          alert('Borrow/Return date cannot be in the past.');
          return;
        }
        this.$emit('save', { ...this.formData });
      }
    }
  };
</script>
  