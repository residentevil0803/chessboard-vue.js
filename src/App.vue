<template>
  <div class="app">
    <Chessboard @square-clicked="updateSelectedSquares" />
    <Sidebar :selected-squares="selectedSquares" />
  </div>
</template>

<script>
import Chessboard from "@/components/Chessboard.vue";
import Sidebar from "@/components/Sidebar.vue";

export default {
  name: "App",
  components: {
    Chessboard,
    Sidebar,
  },
  data() {
    return {
      selectedSquares: [],
    };
  },
  methods: {
    updateSelectedSquares(square) {
      this.selectedSquares.push(square);
    },
  },
};
</script>

<style>
.app {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

@media only screen and (min-width: 820px) {
  .app {
    flex-direction: row;
  }
}
</style>
