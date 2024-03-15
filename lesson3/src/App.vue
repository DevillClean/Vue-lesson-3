<!-- <template>
  
<div>
  <p>originalPrice: {{ originalPrice }}</p>
  <input type="number" v-model="discount">
  <p>discount: {{ discount }}</p>
  <p>finalPrice: {{ finalPrice }}</p>
</div>

<HelloWorld />

</template>

<script>

import { defineComponent, ref, computed } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue'

export default defineComponent({
  name: 'App',

  component: {HelloWorld},
  setup() {
    const originalPrice = ref(200)

    const discount = ref(null)
    const finalPrice = computed(() => {
      return originalPrice.value - discount.value;
    })

    return {
      originalPrice,
      discount,
      finalPrice
    }
  }


  
})


</script>

<style>

</style> -->

<!-- <template>

  <h1>originalPrice: {{ originalPrice }}</h1>
  <input type="number" v-model="discount">
  <h1>discount: {{ discount }}</h1>
  <h1>finalPrice: {{ finalPrice }}</h1>


</template>

<script>
 import { defineComponent,ref, computed } from 'vue';

 export default defineComponent ({
  name: 'App',
  components:{},
  setup(){
    const originalPrice = ref(200)
    const discount = ref(null)

    const finalPrice = computed(() =>{
      return originalPrice.value - discount.value;
    })

    return {
      originalPrice,
      discount,
      finalPrice
    }
  }


 })


</script>


<style>

</style> -->


<template>
  <div class="constainer">
    <p>Message{{ message }}</p>
    <form @submit.prevent="submitForm">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name">
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="email">
      <button type="submit">submit</button>
    </form>

    <ul v-if="submissions.length > 0">
      <li v-for="(submission, index) in submissions" :key="index">
        <p>Name: {{ submission.name }}</p>
        <p>Email: {{ submission.email }}</p>
        <button @click="deleteSubmission(index)">Delete</button>
      </li>
    </ul>


  </div>


</template>

<script>


 export default {
  data(){
    return{
      name: '',
      email: '',
      submissions: []
    };
  },
  methods: {
    submitForm(){
      const newSubmissions = {
        name: this.name,
        email: this.email,
      }
      this.submissions.push(newSubmissions)
      this.name = ''
      this.email = ''
    },
    deleteSubmission(index){
      this.submissions.splice(index, 1)
    },
    showMessage(){
      alert('Hello world')
    }
  },
    computed:{
      message(){
        const count = this.submissions.length;
        if (count === 0){
          return 'No submissions'
        } else if (count === 1){
          return 'One submissions'
        } else {
          return `${count} submissions`
        }
      }
    }
  }




</script>


<style>

</style>