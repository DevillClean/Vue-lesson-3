<template>
  
  <h2>message {{ message }}</h2>
  <form @summit.prevent="submidForm">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="name">
    <label for="name">Email:</label>
    <input type="email" id="email" v-model="email">
    <button type="submit"></button>
  </form>
  <ul v-if="submissions.length > 0">
    <li v-for="(submission, index) in submissions" :key="index"> </li>
    <p>name {{ submissions.name }}</p>
    <p>email {{ submissions.email }}</p>
  </ul>

</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      name: '',
      email: '',
      submissions: []
    };
  },
  methods: {
    submitForm() {
      const newSubmissions = {
        name: this.name,
        email: this.email
      }
      this.submissions.push(newSubmissions)
      this.name = ''
      this.email = ''
    },
    showMessage() {
      alert('hello world')
    }
  },
  computed: {
    message() {
      const count = this.submissions.length;
      if (count === 0) {
        return 'No '
      } else if (count === 1) {
        return '1 submission'
      } else {
        return '${count} $submissions'
      }
    }
  }
}

  
</script>


<style >

</style>
