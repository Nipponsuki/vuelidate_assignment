<template>
  <main class="container">
    <Form />
  </main>
</template>

<script>
import Form from "@/components/Form.vue";

export default {
  components: {
    Form,
  },
};
</script>

<style lang="scss">
$green: #5dbe88;
$blue: #25a1fb;
$lightGrey: #eceff3;
$darkGrey: #a7acb6;
$borderRadius: 4px;

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
html {
  font-size: 62.5%;
}
body {
  font-family: "Cuprum", sans-serif;
}

fieldset {
  border: none;
}

.container {
  height: 100vh;
  background: $lightGrey;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
