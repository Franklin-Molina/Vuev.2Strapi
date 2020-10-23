
<template>

 
   <div>
     
         <div class="img-fluid">
        <img id="imagenes" :src="'http://localhost:1337'+items.imagen.url" class="img-fluid" />
       
    </div>
      
      <div class="details">
     
    
      <h5 class="card-title">{{ items.user.username}}</h5>
     
        
      
      </div>

   </div>
    
  


  
</template>

<script>
export default {
  name: "Imagen",
  props: ["items"],
};
</script>