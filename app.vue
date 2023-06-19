<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Chose your option and "Find Name" button bellow</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1. Chose a Gender</h4>
        <div class="option-button">
          <button
            class="option option-left"
            :class="option.gender === Gender.BOY && 'option-active'"
            @click="option.gender = Gender.BOY"
          >
            Boy
          </button>
          <button
            class="option"
            :class="option.gender === Gender.UNISEX && 'option-active'"
            @click="option.gender = Gender.UNISEX"
          >
            UniSex
          </button>
          <button
            class="option option-right"
            :class="option.gender === Gender.GIRL && 'option-active'"
            @click="option.gender = Gender.GIRL"
          >
            Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2. Chose the name's popularity</h4>
        <div class="option-button">
          <button
            class="option option-left"
            :class="option.popularity === Popularity.TRENDY && 'option-active'"
            @click="option.popularity = Popularity.TRENDY"
          >
            Trendy
          </button>
          <button
            class="option option-right"
            :class="option.popularity === Popularity.UNIQUE && 'option-active'"
            @click="option.popularity = Popularity.UNIQUE"
          >
            Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2. Chose the name's length</h4>
        <div class="option-button">
          <button
            class="option option-left"
            :class="option.length === Length.LONG && 'option-active'"
            @click="option.length = Length.LONG"
          >
            Long
          </button>
          <button
            class="option"
            :class="option.length === Length.ALL && 'option-active'"
            @click="option.length = Length.ALL"
          >
            All
          </button>
          <button
            class="option option-right"
            :class="option.length === Length.SHORT && 'option-active'"
            @click="option.length = Length.SHORT"
          >
            Short
          </button>
        </div>
      </div>
      <button class="primary" @click="computedSelectedName">Find Name</button>
    </div>
    <div class="card-container">
      <div v-for="name in selectedNames" :key="name" class="card">
        <h4>{{ name }}</h4>
        <p>x</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Gender, Popularity, Length, names } from "@/data";

interface OptionState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}
const obj: OptionState = {
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT,
};
const option = reactive<OptionState>({
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT,
});

const computedSelectedName = () => {
  const filteredNames = names
    .filter((name) => name.gender === option.gender)
    .filter((name) => name.popularity === option.popularity)
    .filter((name) => {
      if (option.length === Length.ALL) return true;
      else return name.length === option.length;
    });
  selectedNames.value = filteredNames.map((name) => name.name);
};

const selectedNames = ref<String[]>([]);
</script>

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

.option-active {
  background-color: rgb(249, 87, 89);
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  cursor: pointer;
  padding: 0.75rem 4rem;
  border-radius: 6.5rem;
  border: none;
  font-size: 1rem;
  margin-top: 1rem;
}

.card-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.card {
  background-color: rgb(27, 60, 138);
  width: 28%;
  color: white;
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
}
.card p {
  position: absolute;
  top: -29%;
  left: 92.5%;
  cursor: pointer;
  color: rgba(255, 255, 255, 0.178);
}
</style>
