<template>
  <div class="container">
    <h1 class="text-3xl">Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>

    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button class="option option-left">Boy</button>
          <button class="option">Unisex</button>
          <button class="option option-right">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's popularity</h4>
        <div class="option-buttons">
          <button class="option option-left">Trendy</button>
          <button class="option option-right">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose name's length</h4>
        <div class="option-buttons">
          <button class="option option-left">Long</button>
          <button class="option">All</button>
          <button class="option option-right">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

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
  @apply bg-white border-purple-400 border-2 p-3 w-1/4 text-xl cursor-pointer font-bold;

  &:hover {
    @apply bg-slate-400;
  }
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}

.option-right {
  border-radius: 0 1rem 1rem 0;
}


</style>
