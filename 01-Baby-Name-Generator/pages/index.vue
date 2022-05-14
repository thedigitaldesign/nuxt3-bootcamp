<template>
  <div class="container">
    <h1 class="text-3xl">Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>

    <div class="options-container">
      <Option v-for="(option, index) in components" :key="option.title" :option="option" :options="options" />

      <button class="primary" @click="filterNames">Find names</button>
    </div>

    <ul class="card-container">
      <li class="card" v-for="(name, index) in filteredNames" :key="index">
        {{ name }}
        <span class="close">☠️</span>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { Gender, Popularity, Length, Options, Names } from '../models/Names'

const options: Options = reactive({
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT
})

// Alternative strongly typed object
// const options = reactive<Options>({
//   gender: Gender.GIRL,
//   popularity: Popularity.UNIQUE,
//   length: Length.SHORT
// })

const updateGender = (val) => {
  options.gender = val
}

const updatePopularity = (val) => {
  options.popularity = val
}

const updateLength = (val) => {
  options.length = val
}

const filteredNames = ref<string[]>([])

const filterNames = () => {
  const filter = Names.filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      return options.length === Length.ALL || name.length === options.length
    })
    
  filteredNames.value = filter.map(name => name.name)
}

const components = [
  {
    title: `1) Choose a gender`,
    category: `gender`,
    buttons: [Gender.GIRL, Gender.BOY, Gender.UNISEX]
  },
  {
    title: `2) Choose the name's popularity`,
    category: `popularity`,
    buttons: [Popularity.TRENDY, Popularity.UNIQUE]
  },
  {
    title: `3) Choose name's length`,
    category: `length`,
    buttons: [Length.ALL, Length.LONG, Length.SHORT]
  },
]
</script>

<style scoped lang="less">
.container {
  @apply max-w-4xl m-auto text-center;
}

.options-container {
  @apply bg-slate-300 rounded-md p-2 w-11/12 m-auto mt-12 relative;
}


.primary {
  @apply bg-purple-900 text-white rounded-lg border-none py-3 px-4 mt-6 cursor-pointer;
}

.card-container {
  @apply flex mt-8 flex-wrap justify-around;

  .card {
    @apply bg-orange-400 text-white w-1/4 rounded-md p-2 m-1 relative;
  }

  .close {
    @apply text-black absolute top-0 right-1 cursor-pointer;
  }
}
</style>
