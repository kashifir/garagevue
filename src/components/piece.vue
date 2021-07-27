<template>
  <div class="piece">
    <div class="lightbulb">
      <div class="light"></div>
      <div><img src="https://i.imgur.com/i5AWSel.png" /></div>
    </div>
    <div class="letter">
      <img src="../assets/i.svg" />
    </div>
    <div class="btn" v-show="show">
      <button @click="show = false" class="glow-on-hover" type="button">
        Créer un piece
      </button>
    </div>
    <table class="styled-table" v-show="show">
      <!-- Différentes balises
Balises élémentaires
<table> : crée un tableau
<caption> : légende du tableau (optionnel)
<tr> : ligne du tableau
<th> : cellules d'en-tête du tableau
<td> : cellules du tableau
Balises complémentaires
<thead> : groupe de cellules d'en-tête
<tbody> : groupe de cellules de corps de tableau
<tfoot> : groupe de cellules de pied de tableau -->
      <thead>
        <tr>
          <th>#</th>
          <th>Ref Piece</th>
          <th>Prix</th>
          <th>Stock</th>
          <th>Type Moteur</th>
          <th>Modele</th>
          <th>Nom</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="piece in pieces"
          :key="piece.id"
          v-bind:class="{ trcolor: piece.id % 2 === 0 }"
        >
          <td>{{ piece.id }}</td>
          <td>{{ piece.ref_piece }}</td>
          <td>{{ piece.prix }}</td>
          <td>{{ piece.stock }}</td>
          <td>{{ piece.type_moteur }}</td>
          <td>{{ piece.modele }}</td>
          <td>{{ piece.nom }}</td>
        </tr>
      </tbody>
    </table>
    <div class="newpiece" v-if="!show">
      <form>
        <fieldset>
          <legend>piece</legend>

          <label for="field1">
            <span
              >Ref Piece
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field1"
              v-model="ref_piece"
              value=""
            />
          </label>

          <label for="field2">
            <span
              >Prix
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field2"
              v-model="prix"
              value=""
            />
          </label>

          <label for="field3">
            <span
              >stock
              <span class="required">*</span>
            </span>
            <input
              type="number"
              class="input-field"
              name="field3"
              v-model="stock"
              value=""
            />
          </label>

          <label for="field4">
            <span
              >Type Moteur
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field4"
              v-model="type_moteur"
              value=""
            />
          </label>

          <label for="field5">
            <span
              >Modele
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field5"
              v-model="modele"
              value=""
            />
          </label>
          <label for="field5">
            <span
              >Nom
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field5"
              v-model="nom"
              value=""
            />
          </label>
          <label for="field6">
            <span
              >Marque
              <span class="required">*</span>
            </span>
            <input
              type="text"
              class="input-field"
              name="field6"
              v-model="marque"
              value=""
            />
          </label>
          <div class="btn-next">
            <button @click="addpiece" class="glow-on-hover" type="button">
              Submit
            </button>
          </div>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "piece",
  props: ["pieces"],
  data() {
    return {
      show: true,
      nom: "",
      modele: "",
      type_moteur: "",
      marque: "",
      ref_piece: "",
      prix: "",
      stock: "",
    };
  },
  methods: {
    addpiece: function() {
      this.axios
        .post("http://localhost:3000/pieces/new", {
          nom: this.nom,
          modele: this.modele,
          type_moteur: this.type_moteur,
          marque: this.marque,
          ref_piece: this.ref_piece,
          prix: this.prix,
          stock: this.stock,
        })
        .then((res) => {
          console.log(res.data);
          window.location.reload();
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style scoped>
.trcolor {
  background: #111;
  color: #fff;
  font-size: 18px;
}
.letter {
  width: 80px;
}

.piece {
  background-image: url("../assets/garage.jpeg");
  width: 100%;
  height: 100vh;
  position: relative;
  background-size: cover;
}
.styled-table {
  position: absolute;
  top: 25vh;
  left: 50%;
  transform: translateX(-50%);
  border-collapse: collapse; /*to ensure there is no space between the cell borders*/
  margin: 25px 0;
  font-size: 1em; /* 16px */
  width: 80%;

  border: 2px solid #ccc;
  box-shadow: 10px 5px 35px rgba(17, 17, 17, 0.99);
}

.styled-table thead tr {
  background-color: rgba(17, 17, 17, 0.5);
  color: #fff;
  border: 1px solid #ccc;
  padding: 20px;
  box-shadow: 0px 5px 25px rgba(17, 17, 17, 0.99);
  font-weight: bolder;
  text-align: center;
  height: 40px;
  border-radius: 15px;
}

.styled-table th,
.styled-table td {
  padding: 12px 15px;
}
/* .styled-table tbody tr,
.styled-table tbody tr td {
  border: 3px double black;
  border-right: 3px double red;
  border-bottom: 3px double yellow;
} */
.styled-table tbody tr {
  border-top: 3px double whitesmoke;
  color: white;
  font-size: 18px;
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
.btn button,
.btn-next button,
.btn-prev button,
.btn-submit button {
  color: #fff;
  font-weight: bolder;
  margin: 2px;
}
.btn-next button,
.btn-prev button,
.btn-submit button {
  width: 150px;
}
.btn-next {
  margin-left: 270px;
}
.btn-prev {
  margin-left: -350px;
}
.btn-submit {
  position: absolute;
  left: 60%;
  top: 81%;
}
.newpiece {
  width: 56%;
  max-width: 650px;
  transform: translate(-50%, -50%);
  position: absolute;
  top: 50vh;
  left: 50%;
}
.newpiece label {
  display: block;
  margin-bottom: 10px;
}
.newpiece label > span {
  float: left;
  width: 150px;
  color: blue;
  font-weight: bold;
  font-size: 1em;
  text-shadow: 1px 1px 1px #fff;
  text-align: left;
}
.newpiece fieldset {
  border-radius: 10px;
  margin: 0px 0px 10px 0px;
  border: 1px solid #ccc;
  padding: 20px;

  box-shadow: -0px 5px 25px #111;
}
.newpiece fieldset legend {
  color: #111;
  width: 120px;
  max-height: 120px;
  margin-left: -150px;
  border-radius: 5px 5px 5px 5px;
  padding: 0px 8px 3px 8px;

  box-shadow: 9px 5px 6px #111;

  font-weight: bold;
  font-size: 1em;
}
.newpiece textarea {
  width: 250px;
  height: 100px;
}
.newpiece input[type="text"],
.newpiece input[type="email"],
.newpiece input[type="tel"],
.newpiece input[type="number"] {
  border-radius: 25px;
  border: 1px solid #ccc;
  outline: none;
  color: black;
  padding: 7px 8px 7px 8px;
  box-shadow: inset 1px 1px 4px #111;
  background: #fff;
  font-size: 16px;
  font-weight: bold;
  width: 50%;
}
.newpiece input[type="submit"],
.newpiece input[type="button"] {
  background: #eb3b88;
  border: 1px solid #c94a38;
  padding: 5px 15px 5px 15px;
  color: #ff00c8;
  box-shadow: inset -1px -1px 3px #ff62a7;
  border-radius: 3px;
  font-weight: bold;
}
.required {
  color: red;
  font-weight: normal;
}
.newpiece input:focus {
  background-color: rgba(0, 0, 255, 0.164);
}
.lightbulb {
  position: absolute;
  top: -25px;
  left: 35%;
}

.lightbulb img {
  width: 200px;
  transform: rotate(230deg);
}

.light {
  margin: 0 auto;
  text-align: center;
  position: absolute;
  width: 800px;
  height: 800px;
  margin-top: -200px;
  margin-left: -250px;
  left: 0;
  top: 0;
  -webkit-animation-name: flicker;
  animation-name: flicker;
  -webkit-animation-duration: 8s;
  animation-duration: 8s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
}

.light {
  position: absolute;

  background: radial-gradient(
    ellipse at center,
    rgba(255, 255, 255, 0.6) 0%,
    rgba(255, 255, 255, 0) 40%,
    rgba(255, 255, 255, 0) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#4dffffff', endColorstr='#00ffffff',GradientType=1 );
}

@keyframes flicker {
  from {
    opacity: 0.5;
  }
  4% {
    opacity: 0.7;
  }
  8% {
    opacity: 0.45;
  }
  12% {
    opacity: 0.65;
  }
  16% {
    opacity: 0.3;
  }
  20% {
    opacity: 0.5;
  }
  24% {
    opacity: 0.6;
  }
  28% {
    opacity: 0.25;
  }
  32% {
    opacity: 0.3;
  }
  36% {
    opacity: 1;
  }
  40% {
    opacity: 0.4;
  }
  44% {
    opacity: 0.6;
  }
  48% {
    opacity: 0.35;
  }
  52% {
    opacity: 0.2;
  }
  56% {
    opacity: 0.7;
  }
  60% {
    opacity: 0.5;
  }
  64% {
    opacity: 0.65;
  }
  68% {
    opacity: 0.35;
  }
  72% {
    opacity: 0.5;
  }
  76% {
    opacity: 0.4;
  }
  80% {
    opacity: 0.65;
  }
  84% {
    opacity: 0.4;
  }
  88% {
    opacity: 0.35;
  }
  92% {
    opacity: 0.6;
  }
  96% {
    opacity: 0.3;
  }
  to {
    opacity: 0.5;
  }
}
</style>
