<template>
    <h2>Counter of App component in child component: {{ count }}</h2>
    <button @click="increment">Increment using child component(output)</button>
    <button @click="decrement">Decrement using child component(output)</button>
    <h2>Counter of Child component: {{ counter }}</h2>
    <button @click="incrementCounter">Increment child component counter</button>
    <button @click="decrementCounter">Decrement child component counter</button>
</template>

<script>
export default {
  name: 'ChildComponent',
  data() {
    return {
      counter: 0
    }
  },
  props: ['count', 'increment', 'decrement'],
  computed: {
    cnt() {
      return this.counter
    }
  },
  methods: {
    incrementCounter() {
        this.counter++
        this.$emit('counterchanged', this.counter);
    },
    decrementCounter() {
      this.counter--
      this.$emit('counterchanged', this.counter);
    }
  }
}
</script>

<style>

</style>