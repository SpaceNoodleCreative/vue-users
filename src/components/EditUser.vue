<template>
  <tr v-if="user.showEdit">
    <th scope="row">{{i + 1}}</th>
    <td>
      <input type="text" class="form-control" autocomplete="given-name" placeholder="First name" name="fname" v-model="user.firstName" required/>
    </td>
    <td>
      <input type="text" class="form-control" autocomplete="family-name" placeholder="Last name" name="lname" v-model="user.lastName" required/>
    </td>
    <td>
      <input type="text" class="form-control" placeholder="Job title" name="job" v-model="user.jobTitle" required/>
    </td>
    <td class="text-right">
      <a href="#" @click.prevent="saveEdit()"><i class="fas fa-fw fa-check centered-icon text-primary"></i></a>
      <a href="#" @click.prevent="closeEdit()"><i class="fas fa-fw fa-times centered-icon text-black-50"></i></a>
      <a href="#" @click.prevent.stop="removeUser(i)"><i class="fas fa-fw fa-trash text-danger"></i></a>
    </td>
  </tr>
</template>

<script>
  export default {
    name: 'EditUser',
    props: ['user','i'],
    methods: {
      removeUser(i) {
        this.$parent.users.splice(i, 1);
      },
      saveEdit() {
        this.user.showEdit = false;
        console.log("database communication here");
      },
      closeEdit() {
        this.user.showEdit = false;
      }
    }
  }
</script>
