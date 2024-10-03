<template>
    <div>
      <h2>Children Component</h2>
      <p>Received Age: {{ age }}</p>
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise04Children',
    props: {
      age: {
        type: Number,
        required: true,
      },
    },
    watch: {
      age(newAge, oldAge) {
        console.log(`Age changed from ${oldAge} to ${newAge}`);
      },
    },
    mounted() {
      console.log('Component mounted with initial age:', this.age);
    },
  };
</script>
  
<style></style>
  