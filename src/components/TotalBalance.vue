<template>
  <div :class="['total-value', classColor]">Balance: {{ total }}</div>
</template>

<script>
export default {
  name: 'TotalBalance',
  props: {
    total: {
      type: Number,
      default: 0
    }
  },
  computed: {
    classColor() {
      return {
        "green": this.total > 0,
        "black": this.total === 0,
        "red": this.total <0
      }
    }
  }
}
</script>

<style scoped>
.total-value {
  font-size: 16px;
  text-transform: uppercase;
  padding: 20px;
  text-align: center;
}

.black {
  color: #000;
}

.green {
  color: green;
}

.red {
  color: red;
}
</style>
