<template lang="pug">

#app
   <Header title=" Inspirational quotes"></Header>
    
    
    <div class="card">
        <div class="quote-box"  >
                 
          a(v-if="quote.link" :href="quote.link") {{ quote.body }}
          span(v-else)  {{ quote.body }}
          
        </div>
      
        <v-button  :onClick="showModal">Create Quote </v-button>
            //- <v-button :onClick="deleteQuote"> delete</v-button>
    </div>    
      <div v-show="visible">
       <QuoteForm   :quotes='quotes' > </QuoteForm>
       </div>
        //- :onclick="closeModal"
<!--<PwaNotification />-->
</template>

<script>
import PwaNotification from "./components/PwaNotification.vue";
import { getRandomQuote,getData } from "@/quotes";
import Header from "./components/Header.vue";
import QuoteForm from "./components/QuoteForm.vue";
import Button from "./components/Button.vue";

export default {
  name: "app",
  data() {
    return {
      quote: null,
      visible:false,
      quotes:null,
      
    };
  },
  components: {
    PwaNotification,
    Header,
    QuoteForm,
   'v-button': Button,
  },
  methods: {

     showModal() {
        this.visible = true;
      },
      closeModal() {
        this.visible = false;
      }
    
    },
   
  mounted() {
    // console.log(localStorage);
    // this.quotes=saveOnLocalStorage()
    
    this.quote = getRandomQuote();
    this.quotes = getData()
    // localStorage.setItem('quotes',JSON.stringify(this.quotes))

  },
};
</script>


<style>

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1b1d1f;
  margin-top: 60px;
}
* {
  box-sizing: border-box;
}
.quote-box {

  display: flex; 
  font-family:"Bradley Hand";
  margin: 0 auto; 
  margin-bottom: 30px;
  height: 150px;
  border-top-left-radius: 10px;
  border-bottom-right-radius: 10px;
  box-shadow: 0 6px 8px 0 rgba(0, 0, 0, 0.2); /* this adds the "card" effect */
  padding: 16px;
  text-align: center;
  font-size: 20px;
  background-color: whitesmoke;
  width: 70%;
  
}
span {
  
  display: flex;
  margin: 20px;
  align-items: center;
 
}
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    /* display: block; */
    margin-bottom: 20px;
  }
}

</style>
