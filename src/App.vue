<template>
  <div id="app">
    <XyzTransition appear xyz="fade flip-left perspective-1">
      <h2><a href="https://animxyz.com/" target="_blank">AnimXYZ</a> Library PlayGround</h2>
    </XyzTransition>
    <XyzTransitionGroup appear xyz="fade small out-down out-rotate-right appear-stagger">
      <div class="square" v-for="idx in squareCount" v-show="show" :key="idx">{{ idx }}</div>
    </XyzTransitionGroup>
    <XyzTransition appear xyz="fade down flip-up-50%">
      <div class="square-count">
        Square Count: {{ squareCount }}
      </div>
    </XyzTransition>
    <XyzTransition appear xyz="fade down flip-up-50%">
      <div class="btn-wrapper">
        <button class="add-btn" @click="addSquare">Add!</button>
        <button class="remove-btn" @click="removeSquare">Remove!</button>
        <button class="toggle-btn" @click="toggleSquare">Toggle!</button>
      </div>
    </XyzTransition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      squareCount: 3,
      show: true
    }
  },
  methods: {
    addSquare() {
      if (!this.show) return;
      this.squareCount += 1;
    },
    removeSquare() {
      if (!this.show) return;
      if (this.squareCount === 0) return;
      this.squareCount -= 1;
    },
    toggleSquare() {
      this.show = !this.show;
    }
  },
}
</script>

<style lang="scss" scoped>
@mixin defaultFontStyle() {
  font-size: 18px;
  font-weight: 600;
}

#app {
  h2 {
    text-align: center;
    text-decoration: underline;
    a {
      color: darkblue;
    }
  }
  .square {
    display: inline-block;
    width: 100px;
    height: 100px;
    margin: 10px;
    background-color: #666;
    color: #ddd;
    line-height: 100px;
    text-align: center;
    @include defaultFontStyle();
  }
  .square-count {
    position: fixed;
    left: 15px;
    bottom: 15px;
    @include defaultFontStyle();
  }
  .btn-wrapper {
    position: fixed;
    right: 10px;
    bottom: 10px;
    button {
      outline: none;
      padding: 5px 10px;
      margin: 5px;
      border: 1px solid silver;
      border-radius: 5px;
      box-shadow: 1px 3px 3px rgba(0, 0, 0, .1);
      transition: background-color .2s;
      &:hover {
        cursor: pointer;
        background-color: #ccc;
      }
    }
  }
}
</style>