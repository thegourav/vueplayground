<template>
<section class="todo">
  <h1>My TO DO APP</h1>
  <hr>
  <input type="text" class="todobox" autocomplete="off" autofocus
  placeholder="add your todo task here" v-model="newTodo" @keyup.enter="addTodo" />
  <section v-show= "todoList.length" class="list-main">
   <ul class="todo-list">
      <li v-for="item in todoList">
        <div>
          <input class="toggle" type="checkbox">
          <label>{{ item.name }}</label>
          <button class="destroy">X</button>
        </div>
      </li>
   </ul>
    
  </section>
</section>
</template>

<script>
let counter = 0;
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
          todoList : [],
          newTodo : '',
    }
  },
  methods: {
    addTodo(){
      let value = this.newTodo && this.newTodo.trim();
      if (!value)
          return;
      this.todoList.push({
        id:counter++,
        name: value,
        completed : false
      });
      this.newTodo = "";
    }
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.todobox {
width: 300px;
height: 50px;
padding: 0 15px;
font-size: 20px;
}
</style>
