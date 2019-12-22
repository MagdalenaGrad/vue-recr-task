<template>
  <div>
    <p>
      {{ isVisible ? pbody : pbody.substring(0, 50) }}
      <button
        type="button"
        @click="show"
      >{{ isVisible? "close" : "..." }}</button>
    </p>
  </div>
</template>
<script>
export default {
  props: ["pbody"],
  data: function() {
    return {
      isVisible: false
    };
  },
  methods: {
    show: function() {
      this.isVisible = !this.isVisible;
    }
  }
};
</script>

<style lang="scss" scoped>
button {
  border: none;
  background-color: inherit;
  border-bottom: 1px solid black;
  cursor: pointer;
}
</style>