<template>
<button @click="onClick" class="button">
    <slot> Custom</slot>
</button>
    
</template>
<script>
export default {
   props:{
       onClick:{
           type: Function,
           required:true
       }
   }
}
</script>
<style>

</style>