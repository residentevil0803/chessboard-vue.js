<template>
  <div class="chessboard" :class="{ mobile: isMobile }">
    <div
      v-for="(square, index) in squares"
      :key="index"
      :class="
        (selectedSquares.includes(square) && 'selected') +
        ' square' +
        ((index + parseInt(index / 8)) % 2 ? ' odd' : ' even')
      "
      @click="squareClicked(square)"
    >
      {{ square }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Chessboard",
  data() {
    return {
      squares: [
        "a8",
        "b8",
        "c8",
        "d8",
        "e8",
        "f8",
        "g8",
        "h8",
        "a7",
        "b7",
        "c7",
        "d7",
        "e7",
        "f7",
        "g7",
        "h7",
        "a6",
        "b6",
        "c6",
        "d6",
        "e6",
        "f6",
        "g6",
        "h6",
        "a5",
        "b5",
        "c5",
        "d5",
        "e5",
        "f5",
        "g5",
        "h5",
        "a4",
        "b4",
        "c4",
        "d4",
        "e4",
        "f4",
        "g4",
        "h4",
        "a3",
        "b3",
        "c3",
        "d3",
        "e3",
        "f3",
        "g3",
        "h3",
        "a2",
        "b2",
        "c2",
        "d2",
        "e2",
        "f2",
        "g2",
        "h2",
        "a1",
        "b1",
        "c1",
        "d1",
        "e1",
        "f1",
        "g1",
        "h1",
      ],
      selectedSquares: [],
      isMobile: false,
    };
  },
  mounted() {
    this.checkMobile();
    window.addEventListener("resize", this.checkMobile);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.checkMobile);
  },
  methods: {
    squareClicked(square) {
      if (!this.selectedSquares.includes(square)) {
        this.selectedSquares.push(square);
        this.$emit("square-clicked", square);
      }
    },
    checkMobile() {
      this.isMobile = window.innerWidth < 576;
    },
  },
};
</script>

<style scoped>
.chessboard {
  display: flex;
  flex-wrap: wrap;
  width: 80vw;
  max-width: 600px;
  max-height: 600px;
  flex-grow: 1;
  aspect-ratio: 1;
}

.chessboard.mobile {
  width: 80%;
  height: auto;
  max-width: none;
  max-height: none;
}

.square {
  width: calc(100% / 8);
  height: calc(100% / 8);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1rem;
  cursor: pointer;
  border: 1px;
  border-color: black;
}

.square.even {
  background-color: #b58863;
}

.square.odd {
  background-color: #f0d9b5;
}

.selected {
  background-color: #6a5acd !important;
  box-shadow: inset 0 0 0 1px #000;
}
</style>
