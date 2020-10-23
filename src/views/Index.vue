<template >

<div>
  <div>
  <b-navbar toggleable="md" type="dark" variant="info">
    <b-navbar-brand href="#">NavBar</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#">Link</b-nav-item>
        <b-nav-item href="#" disabled>Disabled</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">ES</b-dropdown-item>
          <b-dropdown-item href="#">RU</b-dropdown-item>
          <b-dropdown-item href="#">FA</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>





  <div class="container mt-4">
    <div class="row">
      <div class="col-12"></div>
    </div>

    <div class="row">
      <div class="col-12 col-sm-12 col-md-6 col-lg-4" v-for="items in imagenes" :key="items.id"  >
        <Imagen :items="items" />
      </div>
    </div>
  </div> 

</div>
  
  

</template>
<script>
import Imagen from "../components/Prueba.vue";
import axios from "axios";

export default {
  name: "Home",
  components: { 
    Imagen 
    },
  data() {
    return {
      imagenes: [],
       user: {}
    };
  },
mounted() {
   
    this.traerimagen();
  },

    methods: {
      

      traerimagen(){

        localStorage.removeItem('user')    
        const tokenverificacion = localStorage.getItem('token')
        axios.get('http://localhost:1337/imagenes/' ,{

          headers: {
          'Authorization': 'Bearer ' + tokenverificacion
        }

        })
        .then((response)=>  {
          this.imagenes = response.data
          console.log(response)
        })
      }


      
    }
   
  /*

   axios
        .get("http://localhost:1337/tags", {
          params,
        })
        .then((response) => {
          this.tags = response.data;
        });
  mounted() {


    fetch("http://localhost:1337/imagenes/")

      .then((res) => res.json())

      .then((data) => {
       
        this.imagenes = data;
         console.log(data);
      });
  },
*/

  
};



</script>
<style >
#col_border {
  text-decoration: none;
}
h1 {
  color: rgb(0, 0, 0);
  text-align: center;
}

.color {
  background: black;
}

.btnhome {
    font-family: Lato, sans-serif;
  text-decoration: none;
width: 1550px;
  border: 5px solid #2c3e50;
  color: #2c3e50;
  display: block;
 
  font-size: 2rem;
  letter-spacing: 0.1rem;
  padding: 1rem;
  position: relative;
  text-decoration: none;
  text-transform: uppercase;
}

.btnhome::before {
  content: "";
  background-color: #E26A6A;
  box-shadow: 10px 10px 0 #F1C40F, 
              20px 20px 0 #3498DB;
  position: absolute;
  left: 0.25rem;
  top: 0.5rem;
  height: 102%;
  width: 102%;
  z-index: -1;
  transition: all 0.4s ease;
}

.btnhome:hover::before {
  box-shadow: none;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
}


</style>