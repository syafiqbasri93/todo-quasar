<template>

  <q-page class="bg-black" >

        <div class="flex justify-center">
          <h4 class="text-white">
            <span style="color:teal">MINIMAL</span> TO DO
          </h4> 
        </div>

    <div class="row bg-transparent justify-center">
       
       <q-input
       dark
       v-model="newTask"
       @keyup.enter="addTask"
       class="col "
       outlined
       bg-color="black"
       placeholder="What needs to be done today?"
       style="max-width: 700px"
       >
      </q-input>

    </div>

  <div class="row q-pt-xl justify-center">
   <q-list dark
      class="col-5"
      style="width: 700px" 
      separator
      >

      <q-item
      class="col-5" 
      v-for="(task, index) in tasks"
      :key="task.title"
      @click="task.done = !task.done"
      :class="{ 'done bg-transparent' : task.done }"
      clickable
      v-ripple
      style="text-transform: capitalize; 
      font-size: 16px; 
      text-white"
      >

        <q-item-section avatar>
          <q-checkbox dark
           v-model="task.done" 
           class="no-pointer-events"
           val="teal" 
           color="teal" />
        </q-item-section>

        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>

        <q-item-selection
         v-if="task.done"
         side>
         <q-btn dark
         @click.stop="deleteTask(index)"
           flat
           round
           dense
           icon="remove" />
         </q-item-selection>

      </q-item>

    </q-list>
  </div>

    <div 
      v-if="!tasks.length"
      class="no-tasks absolute-center">
      <div class="text-h5 text-white text-center">
        No Tasks
      </div>
      
      
    </div> 

  </q-page>

</template>

<script>
export default {

  data() {

    return {

      newTask:'',

      tasks:[
       
      ]
    }
  },

  methods:{
    
    deleteTask(index){
        this.tasks.splice(index, 1)
        this.$q.notify('Task deleted')
      
    },

    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false
      })
      this.newTask= ''
    }

  }
}
</script>

<style  lang="scss">

   .done {
  
     .q-item__label {
       text-decoration: line-through;
       color: white
     }
   }

   .no-tasks {
     opacity: 0.5;
   }

</style>