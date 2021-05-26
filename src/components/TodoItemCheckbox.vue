<template>
  <div>
    <div
      :class="{ checkbox: true, checked: checked }"
      @click="checked = !checked"
    >
      <p>{{ checked ? "✔️" : "" }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TodoItemCheckbox",

    data() {
      return {
        checked: false,
      };
    },

    watch: {
      checked() {
        this.$emit("checkbox-toggle");
      },
    },
  };
</script>

<style scoped>
  input {
    float: left;
  }

  p {
    font-size: 20px;
  }

  .checkbox {
    cursor: pointer;

    height: 30px;
    width: 30px;
    border: 2px solid black;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  .checked {
    background: lightblue;
  }
</style>
