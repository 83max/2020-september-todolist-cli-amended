<template>
    <div class="div-todo-input">
        <input class="todo-input"
               v-model.lazy="typeTodo"
               v-on:keyup.enter="addTask"
               ref="inputRef"
               type="text"
               placeholder="New task..."
               v-bind:class=" { disabledInput: isDisabledInput } "
        >
    </div>
</template>

<script>
    export default {
        name: "todoInput",

        props: {
            isDisabledInput: {
                type: Boolean,
                required: false
            },
        },

        data () {
            return {
                typeTodo:""
            }
        },

        methods: {
            addTask(){
                this.$emit("add-task", {
                        id: Math.round(Math.random() * 100000, 0),
                        text: this.typeTodo,
                        show: false
                    }
                )
                this.typeTodo = "";
            }

        }
    }
</script>

<style scoped>

    .div-todo-input{
        text-align: center;
        padding-top: 15px;
        padding-bottom: 15px;
    }

    .todo-input{
        border: none;
        border-bottom: 1px dashed grey;
        width: 80%;
        font-size: 20px;
        background-color: #eee0;
    }

    .todo-input:focus{
        outline: 0;
    }

    .disabledInput{
        pointer-events: none;
    }

</style>