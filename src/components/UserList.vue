<template>
  <table class="table table-hover mb-4">
    <thead class="bg-light">
      <tr>
        <th style="width: 70px;">#</th>
        <th>First name</th>
        <th>Last name</th>
        <th>Job</th>
        <th style="width: 100px;"></th>
      </tr>
    </thead>
    <tbody>
      <slot v-for="(user, i) in users">
        <tr v-if="!user.showEdit" @click.prevent="editUser(i)">
          <th scope="row">{{i + 1}}</th>
          <td>{{user.firstName}}</td>
          <td>{{user.lastName}}</td>
          <td>{{user.jobTitle}}</td>
          <td class="text-right">
            <a href="#" @click.prevent><i class="fas fa-fw fa-edit text-primary"></i></a>
          </td>
        </tr>
        <edit-user :user='user' :i='i'/>
      </slot>
      <add-user :users='users'/>
    </tbody>
  </table>
</template>

<script>
  import AddUser from './AddUser.vue';
  import EditUser from './EditUser.vue';
  export default {
    name: 'UserList',
    props: ['users'],
    methods: {
      editUser(i) {
        this.users[i].showEdit = true;
      }
    },
    components: {
      'edit-user': EditUser,
      'add-user': AddUser
    }
  }
</script>
