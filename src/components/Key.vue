<template>
  <button :class="`key`">
    {{ sound.letter }}
  </button>
</template>

<script>
export default {
  name: 'key',
  props: ['sound']
}
</script>

<style>

</style>