<template>
  <div>
    <h1>Registro</h1>

    <div class="flex-container mt-4">
      <div class="row mx-4">
        <div id="tamaño" class="container-fluid">
            <form @submit.prevent="register">
      <label for="username">Usuario</label>
      <strong style="color: red"> * </strong>
       <br />
      <input class="col-xs-12 col-sm-12 col-md-12 col-lg-12" type="text" siz size="90" v-model="username" required /> <br />

      <label for="nombre">Nombre </label>
      <strong style="color: red"> * </strong>
       <br />
      <input type="text"  class="col-xs-12 col-sm-12 col-md-12 col-lg-12" size="90" v-model="nombre" required /><br />
      <label for="email">Email </label> <strong style="color: red"> * </strong>
       <br />
      <input type="email"  class="col-xs-12 col-sm-12 col-md-12 col-lg-12" size="90" v-model="email" required /><br />
      <label for="password">Password </label>
      <strong style="color: red"> * </strong>
       <br />
      <input type="password"  class="col-xs-12 col-sm-12 col-md-12 col-lg-12" size="90" v-model="password" required /><br />

      <div v-if="error">
        <div  class="mt-4 alert alert-danger alert-dismissible fade show" role="alert" >
          <strong>Error !</strong> Usuario / Correo Invalido!
          <button
            type="button"
            class="close"
            data-dismiss="alert"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span> <br />
          </button>
        </div>
      </div>

        <div v-if="loading">
           <div  class="mt-4 alert alert-success alert-dismissible fade show" role="alert" >
          <strong> Exito !</strong> Se registro Exitosamente!
          <button
            type="button"
            class="close"
            data-dismiss="alert"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span> <br />
          </button>
        </div>
  
      </div>
   <br>


      <button  class="mb-4 btn btn-dark btn-lg btn-block" type="submit"  id="color">Registrar</button>
    </form>
    <div id="mensaje"></div>
  </div>
          
        </div>
      </div>

    </div>
  
</template>

<script>


import axios from "axios";


export default {
  name: "Registro",
  data() {
    return {
      username: "",
      nombre: "",
      email: "",
      password: "",
      error: false,
      loading : false
     
    };
  },

  methods: {
    register() {
      
     this.error=false
     this.loading= false
    

      axios.post("http://localhost:1337/auth/local/register/",
   
      {
         
        username: this.username,
        nombre: this.nombre,
        email: this.email,
        password: this.password,

        headers: {
          "Content-Type": "application/json",
        },
      })
       .then((response) => {
                this.loading= true
               // this.$router.push('/registro')
            })
      
     .catch((err) =>{
       console.log('Fallo')
       this.error=true
     });
     

    },
  },
};
</script>
<style >
#col_border {
  text-decoration: none;
  color: white;
}

.container {
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
  overflow: hidden;
  width: 500px;
  max-width: 100%;
}
#color {
  background: black;
}
.login__logo {
  width: 64px;
  height: 64px;
}
/*  #tamaño {
            width: 500px;
            max-height: 1000px;
            
        } */

#color {
  background: black;
  margin-bottom: 50px;
}
</style>