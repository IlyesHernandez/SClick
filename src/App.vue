<script>
export default {
  data() {
    return {
      count: 0,
      second: null,
      actualSecond: 0,
      showClickButton: false,
      result: 0,
      showActualClick: false,
      showResult: false
    }
  },
  methods: {
    startGame(){
      let defaultCount = this.count;
      this.showClickButton = true;
      this.showActualClick = true;
      this.showResult = false;
      let seconds = this.second * 1000;
      setTimeout(() => {
        let result = this.count;
        console.log(result)
        this.count = 0;
        this.showClickButton = false;
        this.result = result;
        this.showResult = true;
        this.showActualClick = false;
        this.actualSecond = this.second;
        this.second = null;
      }, seconds)
    }
  }
}
</script>

<template>
  <div class="button">
    <input type="text" v-model="second"/>
    <button @click="startGame()" class="start-btn">Start</button>
    <button v-show="showClickButton" @click="count++">click</button>
    <button @click="count = 0" class="reset-btn">Reset</button>
    <h1 v-show="showResult">You clicked {{ result }} times in {{ actualSecond }} second(s).</h1>
    <h1 v-show="showActualClick">Tu as actuellement cliqué {{ count }} fois.</h1>
  </div>
</template>

<style>
@import "./assets/style.css";

button {
  padding-right: 40px;
  padding-left: 40px;
  padding-top: 15px;
  padding-bottom: 15px;
  font-size: 2.5rem;
  border: none;
  background-color: rgb(51, 40, 209);
  color: white;
  border-radius: 10px;
  cursor: pointer;
  transition-duration: 200ms;
  transition-property: all;
}
button:hover {
  background-color: rgb(65, 54, 218);
}
.button {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 40vh;
  flex-direction: column;
}
.button h1 {
  font-family: Arial,sans-serif;
  color: white;
  font-size: 2.5rem;
}
.button .reset-btn {
  background-color: transparent;
  margin-top: 14px;
  border:1px solid rgb(56, 45, 211);
  font-size: 1.5rem;
  transition-duration: 100ms;
}

.button .reset-btn:hover {
  background-color: rgb(51, 40, 209)
}
.button .start-btn {
  background-color: rgb(17, 183, 64);
  margin-bottom: 14px;
  font-size: 3rem;
}
.button .start-btn:hover {
  background-color: rgb(34, 215, 86);
  margin-bottom: 14px;
  font-size: 3rem;
}

.button input {
  font-size: 1.5rem;
  border-width: none;
  border-style: none;
  padding: 13px;
  border-radius: 0.5rem;
  margin-bottom: 14px;
  border-color: none;
}

.button input:focus {
  border-width: none;
  border-style: none;
  border-color: none;
  background-color: rgb(229, 231, 236);
}
</style>
