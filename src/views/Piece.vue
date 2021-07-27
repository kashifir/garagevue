<template>
  <piece :pieces="pieces" />
</template>

<script>
import piece from "../components/piece";
export default {
  components: { piece },
  data() {
    return {
      pieces: "",
    };
  },
  created: function() {
    this.axios
      .get("http://localhost:3000/pieces/All")
      .then((res) => {
        this.pieces = res.data.pieces;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
