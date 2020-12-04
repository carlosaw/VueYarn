<template>
  <div class="hello">
    <h1>{{ titulo }}</h1>
      <table class="table">
        <thead class="thead-dark">
          <tr>
            <td>#</td>
            <td>Name</td>
            <td>Address</td>
            <td>Phone</td>
            <td>E-mail</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="usuario in usuarios" v-bind:key="usuario.id">
            <td>{{usuario.id}}</td>
            <td>{{usuario.name}}</td>
            <td>{{usuario.address}}</td>
            <td>{{usuario.phone}}</td>
            <td>{{usuario.email}}</td>
            <td>
              <button class="btn btn-info">Editar</button>
            </td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }, data () {
    return {
      titulo: "Tabela",
      usuarios: [
        {id:1, name:'Carlos', address:'New York', phone:36825291, email:'carlos@gmail.com'},
        {id:2, name:'Ana Paula', address:'Rondonópolis', phone:36825291, email:'ana@gmail.com'},
        {id:3, name:'Mara', address:'Várzea Grande', phone:36825291, email:'mara@gmail.com'},
        {id:4, name:'Fulano', address:'Cuiabá', phone:36825291, email:'fulano@gmail.com'}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
