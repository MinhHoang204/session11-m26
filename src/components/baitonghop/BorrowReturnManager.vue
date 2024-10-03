<template>
    <div class="borrow-return-manager">
      <h1>Quản lý mượn trả sách</h1>
      <button @click="openForm">Thêm thông tin</button>
      
      <BorrowReturnTable 
        :records="filteredRecords" 
        @edit="openForm" 
        @delete="confirmDelete"
        @updateStatus="updateStatus"
      />
  
      <!-- Form for Adding/Editing -->
      <BorrowReturnForm 
        v-if="isFormVisible" 
        :record="selectedRecord" 
        @save="saveRecord" 
        @close="closeForm"
      />
  
      <!-- Confirmation Modal for Deletion -->
      <DeleteConfirmationModal 
        v-if="isDeleteModalVisible" 
        @confirm="deleteRecord"
        @cancel="closeDeleteModal"
      />
  
      <!-- Filtering Records by Status -->
      <select v-model="filterStatus">
        <option value="all">All</option>
        <option value="returned">Đã trả</option>
        <option value="not_returned">Chưa trả</option>
      </select>
    </div>
</template>
  
<script>
  import BorrowReturnTable from './BorrowReturnTable.vue';
  import BorrowReturnForm from './BorrowReturnForm.vue';
  import DeleteConfirmationModal from './DeleteConfirmationModal.vue';
  
  export default {
    components: {
      BorrowReturnTable,
      BorrowReturnForm,
      DeleteConfirmationModal
    },
    data() {
      return {
        records: [], // Store borrow/return information
        isFormVisible: false,
        isDeleteModalVisible: false,
        selectedRecord: null, // Record being edited
        filterStatus: 'all',
        recordToDelete: null // Record for deletion
      };
    },
    computed: {
      filteredRecords() {
        if (this.filterStatus === 'all') return this.records;
        return this.records.filter(record => 
          this.filterStatus === 'returned' ? record.status === 'Đã trả' : record.status === 'Chưa trả'
        );
      }
    },
    methods: {
      openForm(record = null) {
        this.selectedRecord = record;
        this.isFormVisible = true;
      },
      closeForm() {
        this.isFormVisible = false;
      },
      saveRecord(record) {
        // Validate and save data to localStorage
        if (this.selectedRecord) {
          // Update existing record
          Object.assign(this.selectedRecord, record);
        } else {
          // Add new record
          this.records.push(record);
        }
        localStorage.setItem('borrowReturnRecords', JSON.stringify(this.records));
        this.closeForm();
      },
      confirmDelete(record) {
        this.recordToDelete = record;
        this.isDeleteModalVisible = true;
      },
      closeDeleteModal() {
        this.isDeleteModalVisible = false;
        this.recordToDelete = null;
      },
      deleteRecord() {
        this.records = this.records.filter(record => record !== this.recordToDelete);
        localStorage.setItem('borrowReturnRecords', JSON.stringify(this.records));
        this.closeDeleteModal();
      },
      updateStatus(record, status) {
        record.status = status;
        localStorage.setItem('borrowReturnRecords', JSON.stringify(this.records));
      }
    },
    mounted() {
      const savedRecords = JSON.parse(localStorage.getItem('borrowReturnRecords'));
      if (savedRecords) {
        this.records = savedRecords;
      }
    }
  };
</script>
  
<style scoped>
  .borrow-return-manager {
    padding: 20px;
  }
</style>
  