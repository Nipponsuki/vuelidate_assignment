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
  font-family: "Ubuntu", sans-serif;
  background: $lightGrey;
}
fieldset {
  border: none;
}

button,
input,
select {
  font-family: inherit;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 1rem 0;

  @media only screen and (max-width: 700px) {
    margin: 0;
  }
}
</style>
