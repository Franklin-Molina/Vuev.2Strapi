
<template>

 
   <div class="box" >
  
    <div class="card">
      <div class="imgBx">
         <img id="galeria" :src="'http://localhost:1337'+items.imagen.url" class="img-fluid" />
       
      </div>
      
      <div class="details">
     <h5 class="card-title">{{ items.created_at}}</h5>
        
      
      </div>
    </div>
  </div>


 

  
</template>

<script>
export default {
  name: "Galeria",
  props: ["items"],
};
</script>

<style>
 body{
 
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: red;
  
  
  font-family: sans-serif;
}
</style>
