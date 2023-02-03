<template>
  <div class="message">
    <p>Error message - {{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
      default: 'default message',
    },
  },
};
</script>

<style lang="scss" scoped>
.message {
  margin: 10px;
  text-align: center;
  color: red;
}
</style>
