<template>
  <p
    class="error-message"
    role="alert"
    title="Это поле обязательно для заполнения"
  >
    <slot></slot>
  </p>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.error-message {
  color: #f2123b;
  font-size: 1.2rem;
  position: absolute;
  bottom: -5px;
  left: 0;
}
</style>
