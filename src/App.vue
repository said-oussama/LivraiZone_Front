<template>
<div class="app" >
  <header>
    <div class="title">
      <img src="./assets/heart.svg" alt="site logo">
      <h1>LivraiZone</h1>
    </div>
    <div class="order">
      <button @click="handleClick('title')"> order by title</button>
   <button @click="handleClick('salary')"> order by salary</button>
   <button @click="handleClick('location')"> order by location</button>

    </div>
  </header>
   
   <JobList :jobs="jobs" :order="order" > </JobList>
</div>
</template>

<script lang="ts">
import { defineComponent, reactive ,ref,toRefs} from 'vue';
import JobList from './components/JobList.vue'
import Job from './types/job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup(){
  //  const state =reactive({
  //   name:'Link', 
  //   age : 25 as string |  number

  //  }) 
  //  state.name='shaun' 
  //  state.age=90

  //  return {...toRefs(state)}

  // const name = ref('Link')
  // const age = ref<number | string>(27) 

  // age.value=10

  // return {name,age}

  const jobs = ref <Job[]>([
    {title: 'farm worker', location :'london' ,salary:3000, id:'1'},
    {title: 'www', location :'london' ,salary:30, id:'2'},
    {title: 'fffff', location :'gabes' ,salary:4000, id:'3'},
    {title: 'rrrr', location :'jandouba' ,salary:5000, id:'4'},
    {title: 'ttttt', location :'tunis' ,salary:6000, id:'5'},

  ])
  const order = ref<OrderTerm>('salary')
  const handleClick = (term: OrderTerm) =>{
    order.value=term

  }

  return {jobs,handleClick,order}

  },
  // data(){
  // return{
  //   name:'Link',
  //   age:25 as number | string
  // }

  // },
  // methods:{
  //  changeName(name : string){
  //   this.name=name
  //   return name
  //  },

  //  changeAge(age : string | number){
  //   this.age=age
  //   return age 
  //  },
  // },
  

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
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }

  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }

  header h1 {
    font-size: 3em;
  }
</style>
