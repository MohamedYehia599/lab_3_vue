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
                   
                   <tr v-for="admin in admins" :key="admin.name">
                      <td>{{admin.name}}</td>
                       <td>{{admin.age}}</td>
                       <td>{{admin.address}}</td>
                       <td><button @click="del(admin)" class="btn btn-danger" >Delete</button></td>
                   </tr>
                  
               </tbody>
       </table>
    </div>
</template>

<script>
import { inject } from '@vue/runtime-core'

    export default {
        name:'adminsView',
        setup(){
            const admins = inject('admins',[])
            return{
                admins,
                del
            }
            function del(admin){
                admins.pop(admin)
            }
        }
    }
</script>

<style scoped>

</style>