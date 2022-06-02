<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

  <div class="container d-flex align-items-center justify-content-center">
    <div>
    <div class=" d-flex justify-content-center">
    <button @click="activeTab='formView'" class="btn btn-primary mx-3 my-3">Form</button>
    <button @click="activeTab='studentsView'" class="btn btn-success mx-3 my-3">Students</button>
    <button @click="activeTab='adminsView'" class="btn btn-danger mx-3 my-3">Admins</button>
    </div>
    
    <div class="main d-flex justify-content-center ">
      <component :is="activeTab"  @send="add"  />
                
    </div>
  
  
  </div>
  </div>
</template>

<script>
import studentsView from './components/studentsView.vue'
import adminsView from './components/adminsView.vue'
import formView from './components/formView.vue'
import { provide, ref } from 'vue'

export default {
  name: 'App',
  components: {
    studentsView,
    adminsView,
    formView
  },
  setup(){
    const activeTab=ref('formView')
    
    let students=ref([])
    let admins=ref([])
    provide('admins',admins.value)
      
    
    provide('students',students.value)
      
    
    return{
      activeTab,
      
      add,admins,students
    }
    function add(data,adminBool,studentBool) {
   if(adminBool.value){
     admins.value.push(data)
     console.log('admin is added')
     console.log(admins.value);
   }
   else if(studentBool.value){
     students.value.push(data)
     console.log('student is added')
     console.log(students.value);
   }
   
   
  }
  }
  

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
