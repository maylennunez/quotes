<template >

<div >
    <div class='form '>
    
      {{this.showQuote}}
     <input type="inputText" placeholder="add quote" v-model="inputText.body"  v-on:keyup.enter="addQuote">
    
         <!-- {{this.quotes}} -->
      </div> 
     
     <v-button  :onClick='addQuote' >Add</v-button>
     <v-button  :onClick='close'  >close</v-button>

  </div>   

    
  
</template>


<script>
 import Button from './Button.vue';

 export default {
    
    data() {
       return {
           visible:true,
           inputText:{
               body: ''
           }
               
       
       }
      
    },
    components:{
     "v-button": Button
    },
       props: 
         ['quotes'],
     
             
        
        
     methods:{
         close() {
             this.visible=false
        this.$emit('close');
      },
     addQuote: function(){
    
        if(this.inputText.body!=''){         
        this.quotes.push(this.inputText)
            console.log(this.quotes);

       localStorage.setItem('quotes',JSON.stringify(this.quotes))
    //    console.log(localStorage.quotes);
        this.inputText.body = ''
        } else {
          console.log("text is empty");

        }

    

   
     }, created(){
         let data= localStorage.getItem('quotes')
         if(data != null){
             this.quotes =JSON.parse(data)
         }
    
    },
    
      
     },
 } 
    
    

</script>



<style>
.form{
 
  margin: auto; 
  margin-top: 30px;
  margin-bottom: 10px;
  height: 150px;
  border-top-left-radius: 10px;
  border-bottom-right-radius: 10px;
  box-shadow: 0 6px 8px 0 rgba(0, 0, 0, 0.2); /* this adds the "card" effect */
  padding: 40px;
  text-align: center;
  background-color: whitesmoke;
  width: 70%;
  
}
</style>