<template>
  <div>
    <h1>{{ titulo }}</h1>
    <div class="filtro">
      Filtro: <input type="search" v-model="textoBuscar">
    </div>
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
          <th><input type="text" v-model="contacto.name" placeholder="Nombre"></th>
          <th><input type="email" v-model="contacto.email" placeholder="Email"></th>
          <th><input type="text" v-model="contacto.address" placeholder="Dirección"></th>
          <th><input type="text" v-model="contacto.phone" placeholder="Teléfono"></th>
          <th><input type="text" v-model="contacto.country" placeholder="País"></th>
          <th><input type="text" v-model="contacto.city" placeholder="Ciudad"></th>
          <th><button class="nuevo" @click="guardarNuevo()">{{ this.contacto.id ? 'Editar' : 'Nuevo' }}</button></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(contacto, index) in contactosComputed" :key="contacto.id">
          <td>{{ contacto.name }}</td>
          <td>{{ contacto.email }}</td>
          <td>{{ contacto.address }}</td>
          <td>{{ contacto.phone }}</td>
          <td>{{ contacto.country }}</td>
          <td>{{ contacto.city }}</td>
          <td>
            <button class="editar" @click="editarContacto(contacto)">Editar</button>
            <button class="eliminar" @click="eliminarContacto(index)">Eliminar</button>
          </td>
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
      textoBuscar: '',
      contacto: {
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
        {
          id: 4,
          name: 'David Lee',
          email: 'david@mail.com',
          address: '1234 Main St, Springfield, IL 62701',
          phone: '217-555-9889',
          country: 'USA',
          city: 'Florida',
        }
      ]
    }
  },
  computed: {
    contactosComputed() {
      return this.contactos.filter(contacto => {
        return contacto.name.toLowerCase().includes(this.textoBuscar.toLowerCase()) ||
          contacto.email.toLowerCase().includes(this.textoBuscar.toLowerCase());
      });
    }
  },
  methods: {
    guardarNuevo() {
      if (this.contacto.id) {
        const index = this.contactos.findIndex(contacto => contacto.id === this.contacto.id);
        this.contactos[index] = { ...this.contacto };
      } else {
        this.contacto.id = this.contactos.length + 1;
        this.contactos.push({
          ...this.contacto,
        });
      }
      this.contacto = {
        id: 0,
        name: '',
        email: '',
        address: '',
        phone: '',
        country: '',
        city: '',
      };
    },
    editarContacto(contacto) {
      this.contacto = { ...contacto };
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

.filtro {
  margin-bottom: 10px;
  text-align: left;
}

input {
  padding: 8px;
  box-sizing: border-box;
  border-radius: 5px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 8px;
  input {
    width: 100%;
  }
}

button {
  padding: 8px;
  border-radius: 5px;
  cursor: pointer;
}

th {
  background-color: #f2f2f2;
  color: #42b983;

  .nuevo {
    background-color: #42b983;
    color: white;
  }
}

td {
  text-align: left;
  border: 1px solid #ddd;

  .editar {
    background-color: #2196F3;
    color: white;
  }

  .eliminar {
    background-color: #f44336;
    color: white;
  }
}
</style>