<template>
    
        <div class="row">
        <input @change="todoTextChange" :value="todoText" class="col form-control mx-2" type="text">
        <button @click="addTodoo" class="btn btn-primary col-sm-1">ADD</button>
    </div>
    
</template>

<script>
import {mapActions} from 'vuex'
export default {
    data() {
        return {
            todoText :""
        }
    },
    methods: {
        ...mapActions(["addTodo"]) ,
        todoTextChange(e){
            this.todoText = e.target.value
        } ,
        addTodoo(){
            this.addTodo({
                id : Math.random() ,
                title : this.todoText
            }) ;
            this.todoText = ""
        }
    },
    
}
</script>

<style scoped>

</style>