<template>
  <tr>
    <td style="width: 70px;"></td>
    <td>
      <input type="text" class="form-control" autocomplete="given-name" placeholder="First name" name="fname" v-model="formData.firstName" required/>
    </td>
    <td>
      <input type="text" class="form-control" autocomplete="family-name" placeholder="Last name" name="lname" v-model="formData.lastName" required/>
    </td>
    <td>
      <input type="text" class="form-control" placeholder="Job title" name="job" v-model="formData.jobTitle" required/>
    </td>
    <td style="width: 100px;">
      <button type="submit" class="btn btn-primary btn-block disabled" v-if="!valid" disabled><i class="fas fa-fw fa-plus"></i> Add user</button>
      <button type="submit" class="btn btn-primary btn-block" v-else @click.prevent="addUser"><i class="fas fa-fw fa-plus"></i> Add user</button>
    </td>
  </tr>
</template>

<script>
  export default {
    name: 'AddUser',
    props: ['users'],
    data() {
      return {
        formData: {
          showEdit: false
        }
      }
    },
    computed: {
      valid() {
        return this.formData.firstName && this.formData.lastName && this.formData.jobTitle
      }
    },
    methods: {
      addUser() {
        let data = {
          firstName: this.formData.firstName,
          lastName: this.formData.lastName,
          jobTitle: this.formData.jobTitle,
          showEdit: this.formData.showEdit
        };
        this.users.push(data);
        this.formData = {};
      }
    }
  }
</script>
