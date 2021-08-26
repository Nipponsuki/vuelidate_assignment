<template>
  <div>
    <h2 class="heading">Клиент успешно создан</h2>
    <Button @click="$emit('again')">Создать</Button>
  </div>
</template>

<script>
import Button from "@/components/Button.vue";

export default {
  components: {
    Button,
  },
};
</script>
<style lang="scss" scoped>
.heading {
  font-size: 3.2rem;
}
</style>
