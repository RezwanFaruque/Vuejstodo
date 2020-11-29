<template>
   <div class="text-center">
     <h1>This is modern todo app</h1>
     <form @submit.prevent>
        <div v-for="todo in todos" :key="todo.id">
            <div :class="{complete:todo.complete}">
              <input type="checkbox" name="todoname" id="todoname" v-model="todo.complete">
              {{todo.name}}
              <button v-on:click="deletetodo(todo.id)" >Delete</button>
            </div>

            
        </div>
     </form>
     

     <h1>Add To</h1>
     <div>
       <form @submit.prevent="addtodo">
          <input type="text" name="todo" v-model="addtodoname">
          <button type="submit">add todo</button>
       </form>
       
     </div>
   </div>
</template>

<script>
export default {
  name: 'Todo',
  data(){

    return{
      addtodoname:'',
      addtodocomplete: false,
      time: '2 hours',
      todos:[
        {
          id: 1,
          name:"Read Laravel Documentation",
          complete: false,
          time: "3 hours",
        
        },
        {
          id: 2,
          name:"Read Node js Documentation",
          complete: false,
          time: "2 hours",
        
        },
        {
          id: 3,
          name:"Read React Documentation",
          complete: false,
          time: "1 hours",
        
        },
        {
          id: 4,
          name:"Read Vue js Documentation",
          complete: false,
          time: "4 hours",
        
        },
      ]
    }
    
  },
  props: {
   
  },

  methods:{
    addtodo(){
      let totaltodo = this.todos.length;

     const toid = totaltodo + 1;

      if(this.addtodoname != ''){
        this.todos.push({
          id: toid,
          name: this.addtodoname,
          complete: this.addtodocomplete,
          time: this.time,

        })
      }

      this.addtodoname = '';
      
    },

  deletetodo(index){
    let id = index-1
    this.todos.splice(id,1);
  }
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.complete{
  text-decoration: line-through;
  color: red;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.text-center{
  text-align: center;
}
</style>
