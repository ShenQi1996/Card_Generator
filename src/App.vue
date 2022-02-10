<template>
  <div class="car_generator">
    <div class="container d-flex text-center justify-content-center align-items-center flex-column">
      <h1 class="header_text">Card Generator</h1>
      <div class=" container input_container d-flex flex-column">
        <div class="row">
          <div class="col-md-10 col-9 d-flex align-items-center box_1">
            <span>Generate
              <input class="_input"  type="number" @change="onChange()" id="Counts"  min="1" max="5" value="">
              random cards, each with
              <input class="_input" type="number" @change="onChange()" id="RC"  min="1" max="5" value="">
            rows/columns.</span>
          </div>
        <div class="d-grid col-md-2">
          <button v-on:click="onClick()" class="btn btn-primary submit_btn text-center" disabled>Generate</button>
        </div>
        </div>
      </div>
    </div>
      <!-- card -->
      <div class="conatiner d-flex align-items-center justify-content-center flex-column ">
        <Cards :cards="this.cards" :geometry="this.geometry"/>
      </div> 
  </div>
</template>



<script>
import Cards from "./components/Cards.vue";

// let number = 0;

export default {
  name: 'App',
  components: {
    Cards
  },
  data(){
     return {
       cards: 0,
      geometry: 0,
     }
  },
  methods:{
        onClick(){
          let number = parseInt(document.getElementById("Counts").value);
          let geometry = parseInt(document.getElementById("RC").value);
          this.cards = number
          this.geometry = geometry
        },

        onChange(){
          let btn = document.querySelector(".submit_btn");
          let number = parseInt(document.getElementById("Counts").value);
          let geometry = parseInt(document.getElementById("RC").value)
          let input1 = false;
          let input2 = false;
          if(isNaN(number)){
            input1 = false;
          }else{
            input1 = true;
          }
          if(isNaN(geometry)){
            input2 = false
          }else{
            input2 = true
          }
          if(input1 === true && input2 === true){
            btn.removeAttribute("disabled")
          }else{
            btn.setAttribute("disabled", true)
          }

        },
  },
}



</script>

<style scoped>
 @import url('https://fonts.googleapis.com/css2?family=Hind:wght@300&display=swap');
 @import url('https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@100;400&display=swap');


  .car_generator{
    position: relative;
    top: 52px;
  }

  .header_text{
    font-style: normal;
    font-weight: bold;
    font-size: 48px;
    font-family: "Roboto Slab";
    width: 343px;
  }

  .input_container{
    background: rgba(255, 255, 255, 1);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 4px;
    padding: 12px;
    font-family: 'Hind', sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 22px;
    color: rgba(0, 0, 0, 1)
  }
  .Counts{
    margin-bottom: 0;
    justify-content: center;
  }

  ._input{
    width: 56px;
    height: 38px;
    border: 1px solid #CED4DA;
    box-sizing: border-box;
    border-radius: 4px;
    padding: 7px 13px;
    margin: 0px 8px;

    /* font-family: "Helvetica Neue"; */
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: rgba(108, 117, 125, 1);
  }

  .submit_btn{
    border-radius: 4px;
    background: #0D6EFD;
    padding: 7px 13px;
    /* font-weight: bold;  not sure aboiut */
    font-family: 'Roboto Slab', serif;
    font-style: normal;
    font-size: 16px;
    line-height: 150%;
  }



  @media only screen and (max-width: 768px) {
    .box_1{
      margin-bottom: 0;
      justify-content: center;
    }
  } 


  @media  only screen and (max-width: 425px) {
    .box_1{
      justify-content: start;
    }
    #Counts, #RC{
      margin-bottom: 12px;
    }
  }

    @media only screen and (max-width: 375px) {
    .box_1{
      justify-content: start;
    }

    #Counts, #RC{
      margin-bottom: 12px;
    }
  } 



</style>
