<template>
  <div class="conversor">
    <h3>
      De:
      <select v-model="selected1" value="Moeda 1">
        <option>USD</option>
        <option>BTC</option>
        <option>EUR</option>
        <option>GBP</option>
        <option>CAD</option>
        <option>BRL</option>
      </select>
      Para:
      <select v-model="selected2" value="Moeda 2">
        <option>USD</option>
        <option>BTC</option>
        <option>EUR</option>
        <option>GBP</option>
        <option>CAD</option>
        <option>BRL</option>
      </select>
    </h3>
    <input type="text" v-model="moeda1_value" v-bind:placeholder="selected1" />
    <input type="button" value="Converter" v-on:click="converter" />
    <h2>{{ moeda2_value }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      moeda1_value: "",
      moeda2_value: 0,
    };
  },
  methods: {
    converter() {
      let de_para = this.selected1 + "_" + this.selected2;

      let url =
        "https://free.currconv.com/api/v7/convert?q=" +
        de_para +
        "&compact=ultra&apiKey=9e4a08e074354e2c273b";
      fetch(url)
        .then((resposta) => {
          return resposta.json();
        })
        .then((json) => {
          let cotacao = json[de_para];
          console.log(cotacao);

          this.moeda2_value = (cotacao * parseFloat(this.moeda1_value)).toFixed(
            2
          );
        });
    },
  },
};
</script>

<style scoped>
.conversor {
  text-align: left;
  padding: 20px;
  max-width: 400px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  border-radius: 15px;
  background-color: #ffffff5e;
}
</style>
