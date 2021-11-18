<script>
export default {
  name: "BaseButton",
};
</script>

<template>
  <!-- This v-on="$listeners" is a way
  to assign events to an element in a component.
  Without it, Vue does not know where to listen
  for the events. -->
  <div class="btn">
      <button v-on="$listeners">
        <slot>Default Click</slot>
      </button>
  </div>
</template>

<style scoped>
  button {
    background: purple;
    color: white;
  }
</style>
