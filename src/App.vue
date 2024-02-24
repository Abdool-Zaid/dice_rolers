<script>
export default {
  data() {
    return {
      range: 20,
      ammount: 1,
      total: 1,
      res: []
    };
  },
  methods: {
    gen_ran(inp) {
      return Math.max(1, Math.round(Math.random() * inp));
    },
    run() {
      this.res = [];
      this.total = 0;
      for (let index = 0; index < this.ammount; index++) {
        const diceValue = this.gen_ran(this.range);
        this.total += diceValue;
        this.res.push(diceValue);
      }
    }
  }
};
</script>

<template>
  <div>
    <div class="input">
      <label for="dice_count">Amount of dice : {{ ammount }}</label>
      <input type="range" name="dice_count" id="dice_count" v-model="ammount" min="1" max="66">
      <label for="range">Range 1- {{ range }}</label>
      <input type="range" name="range" id="range" v-model="range" min="1" max="100">
      <button @click="run">Roll</button>
    </div>
    <div class="output">
      <h1>Total: {{ total }}</h1>
      <div class="die">

        <div v-for="(dice, index) in res" :key="index" class="dice">
        <p>{{ dice }}</p>  
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.input {
  display: flex;
}
.output {
  display: flex;
}
.die{
  display: flex;
  flex-wrap: wrap;
}
.dice {
  background-color: green;
  height: 42px;
  aspect-ratio: 1;
  border-radius: 50%;
  margin: 1%;
display: flex;
align-items: center;
justify-content: center;
}
p{
  color: azure;
}
</style>
