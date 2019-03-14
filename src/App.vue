<template>
  <div id="app">
    <svg viewBox="0 0 120 20" class="title">
      <text x="0" y="12">Brüche addieren</text>
    </svg>
    <div class="term">
      <span>
        <div class="nenner">1</div>
        <hr />
        <div class="zaehler">
          <div class="button minus" @click="dec('a')"></div>
          <span>{{ a }}</span>
          <div class="button plus" @click="inc('a')"></div>
        </div>
      </span>
    </div>
    <div class="term plus"><span>+</span></div>
    <div class="term">
      <span>
        <div class="nenner">1</div>
        <hr />
        <div class="zaehler">
          <div class="button minus" @click="dec('b')"></div>
          <span>{{ b }}</span>
          <div class="button plus" @click="inc('b')"></div>
        </div>
      </span>
    </div>
    <div class="term equal" style=""><span>=</span></div>
    <div class="term result">
      <span>{{ result }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      a: 1,
      b: 1
    };
  },
  computed: {
    result() {
      return 1 / this.a + 1 / this.b;
    }
  },
  methods: {
    dec(x) {
      this[x] -= this[x] === 1 ? 0 : 1;
    },
    inc(x) {
      this[x] += this[x] === 99 ? 0 : 1;
    }
  }
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  background-color: #f7f8f9;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 5vw;
}

svg.title {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: 15px;
  margin-top: 2vw;
}

.zaehler {
  display: flex;
  align-items: center;
  justify-content: center;
}

.zaehler span {
  padding: 0 0vw;
  width: 15vw;
}

.button:before {
  content: "";
  display: flex;
  justify-content: center;
  align-items: center;
  width: 6vw;
  height: 6vw;
  border-radius: 50%;
  border: 1vw solid #2c3e50;
  font-size: 8vw;
  color: #2c3e50;
}

.button.minus:before {
  content: "\2212";
}

.button.plus:before {
  content: "+";
}

hr {
  border: none;
  height: 1vw;
  background-color: #2c3e50;
  border-radius: 2px;
  margin: 2vw 0;
}

.term {
  display: table;
  float: left;
  width: 35vw;
  height: 30vw;
  text-align: center;
  vertical-align: middle;
  font-size: 7vw;
  font-weight: bold;
}

.term.plus {
  width: 18vw;
}

.term.equal {
  clear: both;
  width: 7vw;
  text-align: left;
}

.term.equal span {
  padding-bottom: 1vw;
}

.term.result {
  text-align: left;
  width: 70vw;
}

.term span {
  display: table-cell;
  vertical-align: middle;
}
</style>
