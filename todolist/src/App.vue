<template>
  <v-app id="app"> 
    <h1 >ToDo
      <input style="place:right;background-color:white" type="text" v-model="newTask" placeholder="blablabla">
      <button @click="addNewTask">Add</button>
    </h1>
    
    
    <v-card
    
    class="done"
    v-for="(task,index) in list" 
    :key="index"
    
    v-show="!task.done"
    >
     <button @click=" done(index)">change  </button> {{task.task}}    <button @click="remove(index)">Remove</button>

    </v-card>

    <h1>Done</h1>
    <v-card
    class="unDone" 
    v-for="(task,index) in list" 
    :key="index"
   
    v-show="task.done"
    >
    <button @click="unDone(index)"> change  </button>  {{task.task}}    <button @click="remove(index)" >Remove</button>  

    </v-card>
    
     
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
    
  },
  data(){
    return{
      title:"down",
      list:[
        {
          done:false,
          task:"aaaa"        
        },
        
        {
          done:true,
          task:"bbbb"        
        },
        
        {
          done:false,
          task:"cccc"        
        },
        
      ]
    }
  },
  methods:{
    updateTitle(e){
      this.title = e ;
    },
    done(index){
      return this.list[index].done=true
    },
    unDone(index){
      return this.list[index].done=false
    },
    addNewTask(){
      this.list.unshift({
        done:false,
        task:this.newTask
      }),
      this.newTask=""
    },
    remove(index){
      this.list.splice(index,1)
     
    }
  }
 
};

</script>

<style scoped>
  #app{
    margin:auto;
  }
  .done{
    color:green
  }
  .unDone{
    color:grey;
    
    border-width:10px;
  }
  h1{
    background-color:black ;
    color:white
  }
</style>
