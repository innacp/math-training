<template>
  <div class="alert alert-secondary">
    <h3>{{ x }} + {{ y }} = ?</h3>
    <hr />
    <div class="buttons">
      <button
        class="btn btn-success mx-2"
        v-for="(number, index) in answers"
        @click="onAnswer(number)"
        :key="index"
      >
        {{ number }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["settings"],
  data() {
    return {
      x: this.mtRand(this.settings.from, this.settings.to),
      y: this.mtRand(this.settings.from, this.settings.to),
    };
  },
  computed: {
    good() {
      return this.x + this.y;
    },
    answers() {
      //generates few buttons and answers randomly
      let res = [this.good];

      while (res.length < this.settings.variants) {
        let num = this.mtRand(
          this.good - this.settings.range,
          this.good + this.settings.range
        );

        if (res.indexOf(num) === -1) {
          //if doesn't include this number
          res.push(num);
        }
      }

      const randRes = res.sort(function () {
        const randFactor = Math.random() - 0.5; //from 0 to 1
        return randFactor;
      });
      return randRes;
    },
  },
  methods: {
    onAnswer(num) {
      if (num == this.good) {
        this.$emit("success"); //passing event to App
      } else {
        this.$emit("error", `${this.x} + ${this.y} = ${this.good}!`);
      }
    },
    mtRand(min, max) {
      let diff = max - min;
      return Math.floor(Math.random() * (diff + 1)) + min;
    },
  },
};
// function mtRand(min, max) {
//   //???
//   let diff = max - min;
//   return Math.floor(Math.random() * (diff + 1)) + min;
// }
</script>

<style scoped>
</style>