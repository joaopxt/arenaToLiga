<template>
  <div class="container">
    <h2>Formate seu deck do Arena para a Liga</h2>
    <div class="text-container">
      <textarea
        type="text"
        @input="setTexto"
        :rows="this.counterLines"
        cols="45"
      />
      <img
        src="../assets/arrowRight.png"
        alt="arrow"
        v-if="returnTextoFormatado"
      />

      <p class="formatted-text" v-if="returnTextoFormatado != ''">
        {{ returnTextoFormatado }}
      </p>
    </div>
    <div class="div-button">
      <button @click="triggerFormat">Formatar</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      textoCru: "",
      textoFormatado: "",
      counterLines: 4,
    };
  },
  computed: {
    returnTextoFormatado() {
      return this.textoFormatado;
    },
  },
  methods: {
    removeLast9Chars(lines) {
      return lines
        .split("\n")
        .map((line) => line.slice(0, -9))
        .join("\n");
    },
    triggerFormat() {
      this.textoFormatado = this.removeLast9Chars(this.textoCru);
    },
    countLines(lines) {
      this.counterLines = 4;
      const stringArray = lines.split("\n");
      for (let i = 0; i < stringArray.length; i++) {
        this.counterLines++;
      }
      this.counterLines -= 4;
    },
    setTexto(event) {
      this.textoCru = event.target.value;
      this.countLines(this.textoCru);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Source+Code+Pro:ital,wght@0,200..900;1,200..900&display=swap");

.container {
  display: flex;
  align-items: center;
  justify-items: center;
  flex-direction: column;
}
.formatted-text {
  white-space: pre-line;
  padding-top: 18px;
  padding-bottom: 18px;
  border: 2px solid #9ba5ae;
  border-radius: 6px;
  width: 405px;
}

.text-container {
  display: flex;
  gap: 50px;
}

h2 {
  color: #fefefe;
  font-family: "Source Code Pro";
}

p {
  color: #fefefe;
}

img {
  width: 32px;
  height: 32px;
  align-self: center;
}

button {
  border-radius: 6px;
  box-shadow: 0 4px 6px 0 rgba(0, 0, 0, 0.1);
  background: var(
    --Highlight-color-highlight-color-gradient,
    linear-gradient(95deg, #c3ff88 12.55%, #64ff99 110.63%)
  );
  color: var(--Colors-dark, #001a78);
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  padding: 13px 40px;
  font: 500 16px/150%;
  font-family: "Source Code Pro";
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
}

textarea {
  padding: 18px 16px;
  border: 2px solid #9ba5ae;
  border-radius: 6px;
  font: 16px;
  color: #50555a;
  background-color: #fff;
}

.div-button {
  margin-top: 24px;
  margin-bottom: 24px;
}
</style>
