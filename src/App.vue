<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, onMounted, reactive, warn } from "vue"

const myObject = reactive({
  title: "How to do lists in Vue",
  author: "Jane Doe",
  publishedAt: '2016-04-10'
})

const todos = ref([{ name: "A", isComplete: false }, { name: "B", isComplete: true }])
const count = ref(0)
const name = ref("Vue.js")
// function increment() {
//   count.value++
// }

// onMounted(() => {
//   console.log(`The initial count is ${count.value}`);
// })

function greet(event) {
  alert(`Hello ${name.value}`)
  if (event) {
    alert(event.target.tagName)
  }
}

function say(message) {
  alert(message)
}
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <button @click="increment">Count is: {{ count }}</button>
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
  <ul>
    <template v-for="(todo, index) in todos" :key="todo.id">
      <li v-if="!todo.isComplete">
        {{ todo.name }}
      </li>
    </template>
  </ul>
  <button @click="count++">Add 1</button>
  <p>Count is {{ count }}</p>
  <button @click="greet">Greet</button>

  <button @click="warn('From cannot be submitted yet.', $event)">Say hello</button>
  <button @click="say('bye')">Say bye</button>


  <button @click.right="console.log('dd')">A</button>

  <!-- this will only fire when Ctrl and no other keys are pressed -->
  <button @click.ctrl.exact="onCtrlClick">A</button>

  <!-- this will only fire when no system modifiers are pressed -->
  <button @click.exact="onClick">A</button>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
