<template>
  <client :clients="clients" />
</template>

<script>
import client from "../components/client";
export default {
  components: { client },
  data() {
    return {
      clients: "",
    };
  },
  created: function() {
    this.axios
      .get("http://localhost:3000/client/getAll")
      .then((res) => {
        this.clients = res.data.clients;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
