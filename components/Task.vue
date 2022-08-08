<template>
    <div :class="`task ${taskContent.done ? 'is-completed' : ''}`">
        <h1 class="task-content">{{taskContent.content}}</h1>
        <div class="task-btns">
            <button @click="toggleTask" class="btn done">{{taskContent.done ? 'Undo' : 'Done'}}</button>
            <button @click="deleteTask" class="btn delete">Delete</button>
        </div>
    </div>
</template>

<script>
    export default{
        name:"Task",
        props:['taskContent'],
        methods:{
            toggleTask(){
                this.$store.commit('TOGGLE_TASK', this.taskContent)
            },
            deleteTask(){
                this.$store.commit('REMOVE_TASK', this.taskContent);
            }
        }
    }
</script>

<style>
    .body{
        font-family: 'Urbanist', sans-serif;
    }
    .task{
        padding: 10px;
        border-radius: 10px;
        width: 40%;
        background-color: #76549A;
        margin: 20px 0;

        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .btn{
        font-family: 'Urbanist', sans-serif;
        color: whitesmoke;
        padding: 5px 10px;
        border: none;
        font-size: 1.5rem;
        cursor: pointer;
        border-radius: 5px;
    }

    .done{
        background-color: #3CCF4E;
    }

    .delete{
        background-color: #D61C4E;
    }

    .is-completed .task-content{
        text-decoration: line-through;
    }
</style>