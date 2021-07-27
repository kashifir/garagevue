<template>
  <div class="home">
    <div class="title">
      <h2 class="gradient-text">
        <div class="letter">
          <img src="../assets/i.svg" />
        </div>
        <div class="dot">
          <img src="../assets/dot.svg" />
        </div>
        Garage
      </h2>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Repellat sunt
        quidem animi deleniti rerum. Nemo quaerat, ut quibusdam blanditiis harum
        repudiandae ratione! Deleniti corporis culpa quasi ad ducimus deserunt
        illo.xs
      </p>
    </div>
    <div class="btn">
      <button
        @click="$router.push('/profil')"
        class="glow-on-hover"
        type="button"
      >
        Mon Profil
      </button>

      <!-- <div class="btn-1">
        <button class="glow-on-hover" type="button">Clients</button>
      </div>
      <div class="btn-2">
        <button class="glow-on-hover" type="button">Reparations</button>
      </div>
      <div class="btn-3">
        <button class="glow-on-hover" type="button">Fournisseurs</button>
      </div>
      <div class="btn-4">
        <button class="glow-on-hover" type="button">Pieces</button>
      </div>
      <div class="btn-5">
        <button class="glow-on-hover" type="button">Mon profil</button>
      </div> -->
    </div>
    <div class="more-btn">
      <div class="btn-1">
        <button
          @click="$router.push('/client')"
          class="glow-on-hover"
          type="button"
        >
          Clients
        </button>
      </div>
      <div class="btn-2">
        <button
          @click="$router.push('/reparation')"
          class="glow-on-hover"
          type="button"
        >
          Reparations
        </button>
      </div>
      <div class="btn-3">
        <button
          @click="$router.push('/fournisseur')"
          class="glow-on-hover"
          type="button"
        >
          Fournisseurs
        </button>
      </div>
      <div class="btn-4">
        <button
          @click="$router.push('/piece')"
          class="glow-on-hover"
          type="button"
        >
          Pieces
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>
<style scoped>
.letter {
  width: 90px;
  position: absolute;
  top: -15%;
  left: 37.8%;
}
.dot {
  width: 90px;
  position: absolute;
  top: 25%;
  left: 40%;
}
.gradient-text {
  background: linear-gradient(
    to right,
    red 20%,
    rgb(0, 162, 255) 40%,
    rgba(56, 212, 223, 0.815) 60%,
    #fff 80%
  );
  background-size: 200% auto;
  color: #000;
  background-clip: text;
  text-fill-color: transparent;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: test 1s linear infinite;
}
@keyframes test {
  to {
    background-position: 200% center;
  }
}

.home {
  width: 100%;
  height: 100vh;
  background-image: url("../assets/garage.jpeg");
  background-size: cover;
}
.title {
  position: absolute;
  text-align: center;
  width: 100%;
  top: 150px;
}
.title h2 {
  font-size: 60px;
  margin-bottom: 5px;
  margin-left: 40px;
}
.title p {
  color: wheat;
  width: 80%;
  margin: 0 auto;
  font-size: 16px;
  font-weight: bold;
  text-shadow: 2px 2px black;
}
.glow-on-hover {
  width: 200px;
  height: 50px;
  border: none;
  outline: none;
  color: #111;
  cursor: pointer;
  background: #111;
  position: relative;
  z-index: 0;
  border-radius: 10px;
}
.glow-on-hover:before {
  content: "";
  background: linear-gradient(
    45deg,
    #ff0000,
    #ff7300,
    #fffb00,
    #48ff00,
    #00ffd5,
    #002bff,
    #7a00ff,
    #ff00c8,
    #ff0000
  );
  position: absolute;
  top: -2px;
  left: -2px;
  background-size: 400%;
  z-index: -1;
  filter: blur(5px);
  width: calc(100% + 4px);
  height: calc(100% + 4px);
  animation: glowing 20s linear infinite;
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  border-radius: 10px;
}
.glow-on-hover:active {
  color: #000;
}
.glow-on-hover:active:after {
  background: transparent;
}
.glow-on-hover:active:before {
  opacity: 1;
}
.glow-on-hover:hover:before {
  opacity: 1;
}
.glow-on-hover:after {
  z-index: -1;
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background: #111;
  left: 0;
  top: 0;
  border-radius: 10px;
}
@keyframes glowing {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}

.btn {
  position: absolute;
  top: 65vh;
  left: 40%;
}
.btn button {
  color: #fff;
  font-weight: bolder;
  margin: 2px;
}
/* .btn-1 {
  width: 20%;
  float: left;
}
.btn-2 {
  width: 20%;
  float: left;
}
.btn-3 {
  width: 20%;
  float: left;
}
.btn-4 {
  width: 20%;
  float: left;
}
.btn-5 {
  width: 20%;
  float: left;
} */
.more-btn {
  position: absolute;
  top: 80vh;
  width: 100%;
  display: inline-block;
  left: 0%;
}

.more-btn button {
  color: #fff;
  font-weight: bolder;
}
.btn-1 {
  width: 25%;
  float: left;
}
.btn-2 {
  width: 25%;
  float: left;
}
.btn-3 {
  width: 25%;
  float: left;
}
</style>
