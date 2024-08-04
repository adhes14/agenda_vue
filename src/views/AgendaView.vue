<template>
  <div>
    <h1>{{ titulo }}</h1>
    <table>
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Email</th>
          <th>Dirección</th>
          <th>Teléfono</th>
          <th>País</th>
          <th>Ciudad</th>
          <th></th>
        </tr>
        <tr>
          <th><input type="text" v-model="contactoNuevo.name" placeholder="Nombre"></th>
          <th><input type="text" v-model="contactoNuevo.email" placeholder="Email"></th>
          <th><input type="text" v-model="contactoNuevo.address" placeholder="Dirección"></th>
          <th><input type="text" v-model="contactoNuevo.phone" placeholder="Teléfono"></th>
          <th><input type="text" v-model="contactoNuevo.country" placeholder="País"></th>
          <th><input type="text" v-model="contactoNuevo.city" placeholder="Ciudad"></th>
          <th><button class="nuevo" @click="guardarNuevo()" >Nuevo</button></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(contacto, index) in contactos" :key="contacto.id">
          <td>{{ contacto.name }}</td>
          <td>{{ contacto.email }}</td>
          <td>{{ contacto.address }}</td>
          <td>{{ contacto.phone }}</td>
          <td>{{ contacto.country }}</td>
          <td>{{ contacto.city }}</td>
          <td><button class="eliminar" @click="eliminarContacto(index)">Eliminar</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AgendaView',
  data() {
    return {
      titulo: 'Agenda de contactos',
      contactoNuevo: {
        name: '',
        email: '',
        address: '',
        phone: '',
        country: '',
        city: '',
      },
      contactos: [
        {
          id: 1,
          name: 'Alice Johnson',
          email: 'alice.johnson@example.com',
          address: '1234 Main St, Springfield, IL 62701',
          phone: '217-555-5555',
          country: 'USA',
          city: 'Springfield',
        },
        {
          id: 2,
          name: 'Bob Smith',
          email: 'bob.smith@example.com',
          address: '123 Maple Street',
          phone: '123-456-3210',
          country: 'Canada',
          city: 'Toronto',
        },
        {
          id: 3,
          name: 'Charlie Brown',
          email: 'charlie.brown@example.com',
          address: '123 Elm Street',
          phone: '123-456-7890',
          country: 'Mexico',
          city: 'Mexico City',
        },
      ]
    }
  },
  methods: {
    guardarNuevo() {
      this.contactos.push({
        id: this.contactos.length + 1,
        ...this.contactoNuevo,
      });
      this.contactoNuevo = {
        name: '',
        email: '',
        address: '',
        phone: '',
        country: '',
        city: '',
      };
    },
    eliminarContacto(key) {
      console.log(key);
      this.contactos.splice(key, 1);
    }
  }
}
</script>

<style scoped>
h1 {
  color: #42b983;
  font-size: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 8px;
}

button {
  padding: 8px;
    border-radius: 5px;
    cursor: pointer;
}

th {
  background-color: #f2f2f2;
  color: #42b983;
  input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    border-radius: 5px;
  }
  .nuevo {
    background-color: #42b983;
    color: white;
  }
}

td {
  text-align: left;
  border: 1px solid #ddd;
  .eliminar {
    background-color: #f44336;
    color: white;
  }
}
</style>