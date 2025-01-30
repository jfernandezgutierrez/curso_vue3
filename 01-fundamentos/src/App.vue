<template>
  <div class="container">
     <img src="./assets/logo.svg" alt="Logo vue" width="125" height="125" />
  <small><h1>Hola mundo</h1> </small>

  <hr />

  <h2>Contador: {{ contador }}</h2>
  <button @click="contador++">+1</button>
  <button @click="contador--">-1</button>
  <button @click="contador = 0">Reset</button>
  </div>
 

</template>

<script>
export default {
  data: () => ({ 
    contador:0,
  }),
  watch:{
    contador(){
      if(this.contador==10){
        this.contador=0;
      }
    }
  },
     methods:{

     }

    
  
};
</script>

<style scoped>
.container{
  text-align: center;
}
small{
  color: #666;

}
h2{
  font-size: 2.5rem;
}
h1{
  font-weight: bolder;
}
button{
  cursor: pointer;
  font-size: 1.5rem;
  margin: 0px 6px;
}

</style>
