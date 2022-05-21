<template>
  <div class="app">
    <header>
      <h2>My First Vue/Typescript</h2>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
// eslint-disable-next-line
import { defineComponent, reactive, toRefs, ref } from 'vue';
import JobList from '@/components/JobList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as string | number
    // })

    // state.name = 'Shawn'
    // state.age = 23;

    // return { ...toRefs(state) }

    // const name = ref('Link');
    // const age = ref<string | number>(23);

    // return { name, age }

    const jobs = ref<Job[]>([
      {title: 'Content writing', location: 'Lagos', salary: 13000, id: '1'},
      {title: 'FrontEnd Web Dev', location: 'USA', salary: 45000, id: '2'},
      {title: 'Fullstack Dev', location: 'Abuja', salary: 55000, id: '3'},
      {title: 'Graphics Designer', location: 'Toronto', salary: 22000, id: '4'},
    ])

    const order = ref<OrderTerm>('title');

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }

    return { jobs, handleClick, order }
  },
  methods: { }
});
</script>



<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 1px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>
