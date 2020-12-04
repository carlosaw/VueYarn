<template>
  <div class="hello">
    <h1>{{ titulo }}</h1>
    <div class=container-fluid>
      <div class="alert alert-warning" role="alert" v-show="usuarios.length === 0">
        Não existem registros de usuários!
      </div>
      <table v-show="usuarios.length > 0" class="table table-striped table-hover table-bordered">
        <thead>
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
          <tr v-for="(usuario, index) in usuarios" v-bind:key="usuario.id">
            <td>{{usuario.id}}</td>
            <td>{{usuario.name}}</td>
            <td>{{usuario.address}}</td>
            <td>{{usuario.phone}}</td>
            <td>{{usuario.email}}</td>
            <td>
                <button class="btn btn-info btn-sm" v-on:click="editar(usuario.id)">Editar</button>  
                <button class="btn btn-danger btn-sm" v-on:click="excluir(index)">Excluir</button>
            </td>
            
          </tr>
        </tbody>
      </table>
      <hr/>
      <h1>Adicionar novo usuário</h1>
      <div class="form-group">
        <p>
          <input placeholder="id" type="text"
            v-model="id"
            name="idUsuario"
            class="form-control"
          />
        </p>
        <p>
          <input placeholder="Name" type="text"
            v-model="name"
            name="nameUsuario"
            class="form-control"
          />
        </p>
        <p>
          <input placeholder="Address" type="text"
            v-model="address"
            name="addressUsuario"
            class="form-control"
          />
        </p>
        <p>
          <input placeholder="Phone" type="text"
            v-model="phone"
            name="phoneUsuario"
            class="form-control"
          />
        </p>
        <p>
          <input placeholder="E-mail" type="text"
            v-model="email"
            name="emailUsuario"
            class="form-control"
          />
        </p>
        <button class="btn btn-success" v-on:click="adicionar">Adicionar</button>
      </div>
    </div>
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
      ],
      id:'',
      name:'',
      address:'',
      phone:'',
      email:''
    }
  },
  methods: {
    adicionar() {
      this.usuarios.push({
        id:this.id,
        name:this.name,
        address:this.address,
        phone:this.phone,
        email:this.email
      });
      this.id='',
      this.name='',
      this.address='',
      this.phone='',
      this.email=''
    },
    editar(parametro) {
      this.usuarios.update(parametro);
    },
    excluir(parametro) {
      this.usuarios.splice(parametro, 1);
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
button {
  margin-right: 10px;
}
</style>
