<template>
  <button @click="$emit('click', $event)" :type="type" :disabled="disabled">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "button",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  border: none;
  background: #5dbe88;
  border-radius: 4px;
  font-size: 1.6rem;
  color: #fff;
  padding: 1% 3%;
  cursor: pointer;
  transition: background 0.4s ease;
  margin: 2rem 0;
  width: 10rem;
  height: 3rem;

  &:hover {
    background: #3fb674;
  }

  &:disabled {
    background: #c5ccd7;
    pointer-events: none;
    cursor: not-allowed;
  }

  @media only screen and (max-width: 400px) {
    width: 100%;
    height: 3rem;
  }
}
</style>
