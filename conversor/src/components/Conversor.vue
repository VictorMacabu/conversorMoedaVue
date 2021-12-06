<template>
    <div class="conversor"> 

        <h2>{{moeda1}} Para {{moeda2}}</h2>
        <input type="text" v-model="moeda1_value" v-bind:placeholder="moeda1">
        <input type="button" value="Converter" v-on:click="converter" >
        <h2>{{moeda2_value}}</h2>

    </div>
</template>

<script>

export default {
 name: "Conversor",
 props: ["moeda1","moeda2"],

    data(){
        return{
            moeda1_value: "",
            moeda2_value: 0
        };
    },
    methods:{
        converter(){
            let de_para = this.moeda1 + "_" + this.moeda2;

            let url = "https://free.currconv.com/api/v7/convert?q="+ de_para +"&compact=ultra&apiKey=9e4a08e074354e2c273b";
        fetch(url).then(resposta => {return resposta.json()})
                        .then(json =>{
                            let cotacao = json[de_para];
                            parseFloat(cotacao);
                            console.log(cotacao);
                            
                            this.moeda2_value = (cotacao * parseFloat(this.moeda1_value)).toFixed(2);
                        })
        }
    }
};
</script>

<style scoped>

</style>
