<template>
  <div id="banner">
    <div class="header" id="#Menu">
      <div v-if="logueado">              
        <div class="row menubar mb-3">
          <div class="col-6 menu-logo py-2">
            <img src="@/assets/images/LOGO 1.svg" />
            <img src="@/assets/images/logo.png" />
          </div>
          <div class="col-6 menu-links py-3">
            <nav class="navbar navbar-expand-lg navbar-light">
              <div class="container-fluid">
                <div class="collapse navbar-collapse" id="navbarNav">
                  <ul class="navbar-nav">
                    <li class="nav-item">
                      <router-link to="/portafolioServicios" class="nav-link mx-4"
                        >Servicios</router-link
                      >
                    </li>
                    <li class="nav-item">
                      <button type="button" @click="logOut"> Salir</button> 
                    </li>
                    
                  </ul>
                  
                </div>
              </div>
            </nav>
          </div>
        </div>
      </div>
      <div v-if="!logueado">
        <div class="row menubar mb-3">
          <div class="col-6 menu-logo py-2">
            <img src="@/assets/images/LOGO 1.svg" />
            <img src="@/assets/images/logo.png" />
          </div>
          <div class="col-6 menu-links py-3">
            <nav class="navbar navbar-expand-lg navbar-light">
              <div class="container-fluid">
                <div class="collapse navbar-collapse" id="navbarNav">
                  <ul class="navbar-nav">
                    <li class="nav-item">
                      <router-link
                        to="/"
                        class="nav-link active mx-5"
                        aria-current="page"
                        >Inicio</router-link
                      >
                    </li>
                    <li class="nav-item">
                      <router-link to="/portafolioServicios" class="nav-link mx-4"
                        >Servicios</router-link
                      >
                    </li>
                    <li class="nav-item">
                      <router-link to="/noticias" class="nav-link mx-4"
                        >Noticias</router-link
                      >
                    </li>
                    <li class="nav-item">
                      <router-link to="/equipo" class="nav-link mx-4"
                        >Equipo</router-link
                      >
                    </li>
                    <li class="nav-item">
                    <router-link to="/home" class="nav-link mx-4"
                        >prueba</router-link
                      >
                    </li>
                    <li class="nav-item">
                    <router-link to="/navbar" class="nav-link mx-4"
                        >barr</router-link
                      >
                    </li>
                  </ul>
                  
                </div>
              </div>
            </nav>
          </div>
      </div>
    </div>

    <div class="container">
      <h1 class="titulos"> Hola {{datosUsuario.nombres}}, Bienvenid@ a Agendy Nails</h1>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data(){
    const datosUsuario = JSON.parse(localStorage.getItem('datosUsuario')) || {}
    const token = localStorage.getItem('token') || null
    const logueado = token != null
    console.log(logueado)

    datosUsuario.logueado = logueado
    console.log('datos usuario en inicio', datosUsuario)
    const logOut = async () =>  {
      await localStorage.clear()
      location.replace('/')
      this.$router.push({ name: home })

    }
    return {
      logueado,
      datosUsuario,
      logOut
    }

  },
    

  }



</script>

<style scoped>
.titulos {
  font-family: verdana;
  font-size: 60px;
  color: #b02b9b;
}
#banner {
  background-color: #FAF4EB;
}
</style>