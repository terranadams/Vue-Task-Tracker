<template>
  <button @click="onClick()" :style="{ backgroundColor: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: "ButtonVue",
  //   props: ['text', 'color']
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
        console.log(this.text)
    }
  }
};
</script>
