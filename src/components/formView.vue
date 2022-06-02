<template>
    <div class="d-flex flex-column">
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Name </label>
            <input type="text" v-model="name" class="form-control" id="exampleFormControlInput1" placeholder="john wick">
        </div>
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Age </label>
            <input type="Number" v-model="age" class="form-control" id="exampleFormControlInput1" >
        </div>
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Address </label>
            <input type="email" v-model="address" class="form-control" id="exampleFormControlInput1" placeholder="5,Mostafa Mohamed,st,Smouha,Alexandria,Egypt">
        </div>
        <div class="form-check">
            <input type="checkbox" class="form-check-input " v-model="adminBool" >
            <label class="form-check-label" for="">
                Admin 
            </label><br>
            <input type="checkbox" class="form-check-input " v-model="studentBool"  >
            <label class="form-check-label " for="">
                 Student 
            </label>
        </div>
        
       <div class="d-flex justify-content-center">
        <button style="width:50px;" class="btn btn-success mt-5" @click="sendUser" >Add </button>
        </div>
     
       
    </div>
</template>

<script>
import { ref, toRefs,reactive } from 'vue'

    export default {
      name:'formView' ,
      emits:['send'],
      
      setup(props,context){
          const formValues = reactive({
                 name:'',
                  age:0,
                  address:''
          })
           const adminBool=ref(false)
            const studentBool=ref(false)
            let err=ref(false)
          return{
                ...toRefs(formValues),
                adminBool,
                studentBool,
                err,
                sendUser
          }
          function sendUser(){
              
              context.emit('send',formValues,adminBool,studentBool)
              
          }
      }
    }
</script>

<style scoped>

</style>