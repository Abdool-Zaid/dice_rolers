<script>
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap.bundle.min.js";

export default {
  data() {
    return {
      range: 20,
      ammount: 1,
      total: 1,
      res: [],
      r: 0,
      g: 128,
      b: 0,
      a: 1,
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
    },
    alt_colour() {
      let el = document.querySelector(".dice");
      el.style.backgroundColour = `rgba(${r},${g},${b},${a})`;
      console.log("colour should've changed");
    },
  },
};
</script>

<template>
  <!-- Modal -->
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-scrollable">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <!-- colour changer -->
          <div class="d-flex flex-column">
            <div class="dice"><p>1</p></div>
            <label for="dice_count">r </label>
            <input
              type="range"
              name="r"
              id="r"
              v-model="r"
              min="0"
              max="255"
              @change="alt_colour()"
            />
            <label for="dice_count">g </label>
            <input
              type="range"
              name="g"
              id="g"
              v-model="g"
              min="0"
              max="255"
              @change="alt_colour()"
            />
            <label for="dice_count">b </label>
            <input
              type="range"
              name="b"
              id="b"
              v-model="b"
              min="0"
              max="255"
              @change="alt_colour()"
            />
            <label for="dice_count">a </label>
            <input
              type="range"
              name="a"
              id="a"
              v-model="a"
              min="0"
              max="255"
              @change="alt_colour()"
            />
          </div>
          <!-- colour changer -->
          <!-- config goes here -->
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
        </div>
      </div>
    </div>
  </div>

  <div>
    <div class="input">
      <label for="dice_count">Amount of dice : </label>
      <input
        type="number"
        name="dice_count"
        id="dice_count"
        v-model="ammount"
        min="1"
        max="66"
      />
      <label for="range">Range 1- </label>
      <input
        type="number"
        name="range"
        id="range"
        v-model="range"
        min="1"
        max="100"
      />
      <button @click="run">Roll</button>
    </div>
    <div class="output">
      <!-- Button trigger modal -->
      <button
        type="button"
        class="btn btn-primary"
        data-bs-toggle="modal"
        data-bs-target="#exampleModal"
      >
        config
      </button>
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
.die {
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
p {
  color: azure;
}
</style>
