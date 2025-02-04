<template>
  <h1>This is simple counter application.</h1>
  <h2>Counter from App component: {{ count }}</h2>
  <button @click="incrementCount()">Increment using App component</button>
  <button @click="decrementCount()">Decrement using App component</button>
  <ChildComponent ref="child" @counterchanged="counterChanged" :count=count :increment="incrementCount" :decrement="decrementCount"> </ChildComponent>
  <h2>Counter of child component in App component: {{ counter }}</h2>
  <button @click="incrementCounter()">Increment Child component counter using App component</button>
  <button @click="decrementCounter()">Decrement Child component counter using App component</button>
</template>

<script>
import ChildComponent from './components/Child.vue';

export default {
  name: 'App', 
  components: {
    ChildComponent
  },
  data() {
    return {
      count: 0,
      counter: 0
    }
  },
  methods: {
    incrementCount() {
      this.count++
    },
    decrementCount() {
      this.count--
    },
    counterChanged(value) {
      this.counter = value
    },
    incrementCounter() {
      this.$refs.child.incrementCounter()
    },
    decrementCounter() {
      this.$refs.child.decrementCounter()
    }
  }
}
</script>

<style>
#app {
  background: wheat;
}
</style>
