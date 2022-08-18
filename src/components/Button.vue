<template>
  <button :style="{ backgroundColor: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: "ButtonVue",
  //   props: ['text', 'color']
  props: {
    text: String,
    color: String,
  },
};
</script>
