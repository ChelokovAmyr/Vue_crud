<template>
  <div id="employee-table">
    <p>{{name}}</p>
    <p v-if="employees.length < 1" class="empty-table">No employees</p>
    <table v-else>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <td>  
            <button @click="editMode(employee.id)">Edit</button>
            <button @click="$emit('delete:employee', employee.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'employee-table',
    props: {
      employees: Array,
      name
    }
  }
</script>

<style scoped>
  button {
    margin: 0 0.5rem 0 0;
  }
</style>