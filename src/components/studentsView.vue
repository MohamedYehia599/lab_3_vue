<template>
    <div>
       <table class="table table-striped ">
           <thead class="thead-inverse|thead-default">
               <tr>
                   <th>Name</th>
                   <th>Age</th>
                   <th>Address</th>
                   <th>Delete</th>
               </tr>
               </thead>
               <tbody>
                   
                   <tr v-for="student in students" :key="student.name">
                       
                     <td>{{student.name}}</td>
                        <td>{{student.age}}</td>
                        <td>{{student.address}}</td>
                       <td><button class="btn btn-danger" @click="del(student)" >Delete</button></td>
                   </tr>
                  
               </tbody>
       </table>
     
        
        
    </div>
</template>

<script>
import  { inject } from 'vue'

    export default {
        name:'studentsView',
      setup(){
             const students =inject('students',[])

          return{
                students,
                del
                
          }
          function del(student){
              students.pop(student)
          }
      }

    }
</script>

<style scoped>

</style>