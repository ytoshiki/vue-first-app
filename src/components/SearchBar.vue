<template>
  <div>
    <input @input="onChange" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onChange: function(e) {
      this.$emit('termChange', e.target.value);
    }
  }
};
</script>

<style></style>
