<template>
  <div>
    <div class="row my-3 text-align-center">
      <p v-if="!editing" class="col">{{ todo.title }}</p>
      <input v-else type="text" :value="todoText" @change="textChange" class="col form-control"/>
      <button @click="editTodo(todo)" class="btn btn-primary col-sm-1 mx-2">{{editing ? 'UPDATE' : 'EDIT'}}</button>
      <button @click="deleteTodo(todo.id)" class="btn btn-danger col-sm-1">DELETE</button>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
export default {
  props: {
    todo: {},
  },
  data() {
      return {
          todoText :"" ,
          editing : false
      }
  },
  methods: {
      ...mapActions(["deleteTodo" ,"updateTodo"]) ,
      textChange(e){
         this.todoText = e.target.value
      },
      editTodo(todo){
          this.editing = this.editing == true ? false : true ;
          if(this.editing){
              this.todoText = todo.title ;
              this.updateTodo(todo)
          }
          else {
              todo.title = this.todoText
          }
      }
  },
};
</script>

<style scoped></style>
