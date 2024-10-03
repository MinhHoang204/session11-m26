<template>
    <table>
      <thead>
        <tr>
          <th>STT</th>
          <th>Tên sách</th>
          <th>Sinh viên mượn</th>
          <th>Ngày mượn</th>
          <th>Ngày trả</th>
          <th>Trạng thái</th>
          <th>Chức năng</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(record, index) in records" :key="record.id">
          <td>{{ index + 1 }}</td>
          <td>{{ record.bookTitle }}</td>
          <td>{{ record.borrowerName }}</td>
          <td>{{ record.borrowDate }}</td>
          <td>{{ record.returnDate }}</td>
          <td>
            <select v-model="record.status" @change="updateStatus(record, record.status)">
              <option value="Đã trả">Đã trả</option>
              <option value="Chưa trả">Chưa trả</option>
            </select>
          </td>
          <td>
            <button @click="$emit('edit', record)">Sửa</button>
            <button @click="$emit('delete', record)">Xóa</button>
          </td>
        </tr>
      </tbody>
    </table>
</template>
  
<script>
  export default {
    props: ['records'],
    methods: {
      updateStatus(record, status) {
        this.$emit('updateStatus', record, status);
      }
    }
  };
</script>
  