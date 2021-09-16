<template>
  <button
    class='flex mx-auto mt-6 text-white border-0 py-2 px-5 focus:outline-none hover:bg-indigo-600 rounded shadow-2xl'
    @click="$emit('change-event', url)">{{ name }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    url: {
      type: String,
    },
    name: {
      type: String
    }
  }
}
</script>

<style scoped>

</style>
