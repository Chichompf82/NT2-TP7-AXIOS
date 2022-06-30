<template>
  <section class="src-componentes-usuario">
    <div class="jumbotron">
      <h2>Usuarios Disponibles</h2>
      <hr>
      <hr>
      <br>

      <div v-if="usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
          <tr v-for="(usuario, index) in usuarios" :key="index">
              
              <td>{{ usuario.nombre }}</td>
              <td>{{ usuario.edad }}</td>
              <td>{{ usuario.email }}</td>
          </tr>
        </table>
        <h5 class="alert alert-primary"> {{usuarios.length}} usuario(s) diponible(s).</h5>
      </div>
      <h4 v-else class="alert alert-danger text-center">No se encontraron Usuarios</h4>

     </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-usuario',
    props: [],
    mounted () {
      this.getUsuarios()
    },
    data () {
      return {
        url: 'https://629f50a48b939d3dc294f550.mockapi.io/usuarios2',
        usuarios: []
      }
    },
    methods: {
      
      async getUsuarios() {
        try{
          let { data } = await this.axios(this.url)
          this.usuarios = data
        }
        catch(error){
          console.error('Error Axios', error)
        }
      }

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-componentes-usuario {

  }

  .jumbotron {
    background-color: rgb(5, 24, 25);
    color: white;
  }

  hr {
    background-color: #bbb;
  }  
</style>
