<template>
    <div>
      <h2>Children Component</h2>
    </div>
</template>
  
<script>
  export default {
    name: 'Exercise05Children',
    beforeUnmount() {
      console.log('beforeUnmount: Component is about to be unmounted');
    },
    unmounted() {
      console.log('unmounted: Component has been unmounted');
    },
  };
</script>
  
<style></style>
  