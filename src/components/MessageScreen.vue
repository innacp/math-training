<template>
  <div class="alert" :class="'alert-' + type">
    <h2>{{ text }}</h2>
    <hr />
    <button class="btn btn-primary" @click="$emit('onNext')">Continue</button>
  </div>
</template>

<script>
export default {
  props: ["type", "text"], //parameters received by the component from App (passing via props to h2)
};
</script>

<style>
.alert {
  text-align: center;
}
h3,
.btn {
  margin: 20px 15px;
}
</style>