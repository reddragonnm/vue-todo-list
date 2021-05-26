<template>
  <div>
    <div class="checkbox" @click="checked = !checked">
      <i class="fas fa-check" v-show="checked"></i>
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

  i {
    color: rgb(141, 235, 1);
    font-size: 23px;
  }

  .checkbox {
    cursor: pointer;

    height: 30px;
    width: 30px;
    border: 2px solid black;

    display: flex;
    justify-content: center;
    align-items: center;

    transition: all 0.2s ease;
  }

  .checkbox:hover {
    background: rgb(230, 230, 230);
  }
</style>
