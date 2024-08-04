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
        </tr>
      </thead>
      <tbody>
        <tr v-for="contacto in contactos" :key="contacto.id">
          <td>{{ contacto.name }}</td>
          <td>{{ contacto.email }}</td>
          <td>{{ contacto.address }}</td>
          <td>{{ contacto.phone }}</td>
          <td>{{ contacto.country }}</td>
          <td>{{ contacto.city }}</td>
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
  }
}
</script>

<style scoped>
h1 {
  text-align: left;
  color: #42b983;
  font-size: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
  color: #42b983;
}

td {
  text-align: left;
}
</style>