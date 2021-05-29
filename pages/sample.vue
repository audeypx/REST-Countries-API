<template>
  <div class="px-24 py-12">
    <button class="bg-green-400 py-2 px-4 text-white" @click="add">Add</button>
    <!-- <button class="bg-green-400 py-2 px-4 text-white" @click="add">Add</button> -->

    <span v-if="count === 1" class="text-2xl"> Drey </span>
    <span v-if="count === 2" class="text-2xl"> Audrey </span>
    <span v-if="count === 3" class="text-2xl"> Ozioma </span>
  </div>
</template>

<script>
export default {
  name: 'Sample',
  data() {
    return {
      count: 0,
    }
  },

  methods: {
    add() {
      if (this.count === '') return
      this.count++
    },
  },
  mounted() {
    setInterval(this.add, 1500)
  },
}
</script>
