<template>
  <div class="alert alert-secondary">
    <h3>Are you ready?</h3>
    <button class="btn btn-success" @click="$emit('onStart')">Start</button>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.alert {
  text-align: center;
}
h3,
.btn {
  margin: 20px 15px;
}
</style>