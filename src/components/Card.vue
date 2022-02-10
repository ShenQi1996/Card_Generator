<template>
    <div class="container d-flex justify-content-center align-items-center flex-column ">
        <div v-for="i in this.geometry" :key="i" class="row">
            <div class="col d-flex p-0 title" v-for="Char in this.Rresult.slice(((i-1)*this.geometry), this.geometry+(this.geometry * (i-1)))" :key="Char">{{Char}}</div>
        </div>
    </div>
</template>


<script>

export default {
    name: "Card",
    props: {
        geometry: Number,
    },
    data(){
        return{
            Rresult: Array
        }
    },
    methods: {
        generate(){
            const alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
            const totoal = this.geometry * this.geometry;
            let alpLength = alphabet.length;
            let result = "";
            let i = 0;
            while(i < totoal){
                let tem = alphabet.charAt(Math.floor(Math.random() * alpLength))
               if(!result.includes(tem)){
                   result += tem
                   i++;
               }
            }
            this.Rresult = result.split("");
       }

    },
    created(){
        this.generate()
    },
    updated(){
        this.generate()
    }

}
</script>

<style scoped>
.title{
    min-width: 60px;
    min-height: 60px;
    background: #FFFFFF;
    justify-content: center;
    align-content: center;
    text-align: center;
    flex-direction: column;

    font-family: "Roboto Slab";
    font-style: normal;
    font-weight: 900;
    font-size: 36px;
    line-height: 47px;
    margin-right: 12px;
    margin-bottom: 12px;
    color: #000000;
    transition: transform 1s;
}
.title:hover{
   transform: scale(1.2);
}
</style>

