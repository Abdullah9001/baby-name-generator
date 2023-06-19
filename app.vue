<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Chose your option and "Find Name" button bellow</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1. Chose a Gender</h4>
        <div class="option-button">
          <button class="option option-left">Boy</button>
          <button class="option">UniSex</button>
          <button class="option option-right">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2. Chose the name's popularity</h4>
        <div class="option-button">
          <button class="option option-left">Trendy</button>
          <button class="option option-right">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2. Chose the name's length</h4>
        <div class="option-button">
          <button class="option option-left">Long</button>
          <button class="option">All</button>
          <button class="option option-right">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: auto;
  text-align: center;
}
h1 {
  font-size: 3rem;
}
.options-container {
  background-color: rgb(255, 238, 236);
  padding: 1rem;
  border-radius: 2rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.option-container {
  margin-bottom: 2rem;
}

.option {
  background-color: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  font-size: 1rem;
  width: 12rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 600;
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}
.option-right {
  border-radius: 0 1rem 1rem 0;
}
</style>
