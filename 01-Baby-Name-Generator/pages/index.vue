<script setup lang="ts">
enum Gender {
  GIRL = 'Girl',
  BOY = 'Boy',
  UNISEX = 'Unisex'
}

enum Popularity {
  TRENDY = 'Trendy',
  UNIQUE = 'Unique'
}

enum Length {
  LONG = 'Long',
  ALL = 'All',
  SHORT = 'Short'
}

interface Options {
  gender: Gender,
  popularity: Popularity,
  length: Length
}

const options: Options = reactive({
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT
})

// Alternative
// const options = reactive<Options>({
//   gender: Gender.GIRL,
//   popularity: Popularity.UNIQUE,
//   length: Length.SHORT
// })
</script>

<template>
  <div class="container">
    <h1 class="text-3xl">Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>

    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button class="option option-left" :class="options.gender === Gender.BOY && `option-active`">Boy</button>
          <button class="option" :class="options.gender === Gender.UNISEX && `option-active`">Unisex</button>
          <button class="option option-right" :class="options.gender === Gender.GIRL && `option-active`">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's popularity</h4>
        <div class="option-buttons">
          <button class="option option-left" :class="options.popularity === Popularity.TRENDY && `option-active`">Trendy</button>
          <button class="option option-right" :class="options.popularity === Popularity.UNIQUE && `option-active`">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose name's length</h4>
        <div class="option-buttons">
          <button class="option option-left" :class="options.length === Length.LONG && `option-active`">Long</button>
          <button class="option" :class="options.length === Length.ALL && `option-active`">All</button>
          <button class="option option-right" :class="options.length === Length.SHORT && `option-active`">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script></script>

<style scoped lang="less">
.container {
  @apply max-w-4xl m-auto text-center;
}

.options-container {
  @apply bg-slate-300 rounded-md p-2 w-11/12 m-auto mt-12 relative;
}
.option-container {
  @apply mb-8;
}

.option {
  @apply bg-white border-purple-500 border-2 p-3 w-1/4 text-xl cursor-pointer;

  &:hover {
    @apply bg-slate-400;
  }
}

h4 {
  @apply font-bold;
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}

.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  @apply bg-purple-300 text-white;
}
</style>
