<template>
    <div>
        <div class="divRemaining"
             v-for="item in remainingTodos" :key="item.id"
        >
            <span>
                <input type="checkbox"
                       class="checkboxClass"
                       v-bind:id="item.id"
                       v-on:click="checkTask(item)"
                >
                <label v-bind:class="{ disabledCheckbox: isDisabledCheckbox }"
                       class="checkboxLabel"
                       v-bind:for="item.id">
                </label>
            </span>
                <label
                        v-bind:id="item.id"
                        class="labelRemainingTodo"
                        v-bind:contenteditable="isContentEditable"
                        v-on:dblclick="editTodoDblClick(item.id)"
                        v-on:keydown.prevent.enter="editTextInLi">
                {{item.text}}</label>
            <span
                    class="fa fa-trash-o"
                    aria-hidden="true"
                    v-bind:class=" {disableDeleteBtn: isDisableDeleteBtn} "
                    v-on:click="deleteTodo(item.id)">
            </span>
        </div>
    </div>
</template>

<script>
    export default {

        name: "todoRemainingTodos",

        props: {
            remainingTodos: {
                type: Array,
                required: false
            },
            isContentEditable: {
                type: Boolean,
                required: true
            },
            passId: {
                type: Number,
                required: false
            },
            isDisableDeleteBtn: {
                type: Boolean,
                required: true
            },
            isDisabledCheckbox: {
                type: Boolean,
                required: true
            },
        },

        data () {
            return {
                yesNoShow: false,
                x: "",
                y: null,
            }
        },
        methods: {
            checkTask(item){
                this.$emit("check-task", item)
            },
            deleteTodo(item){
                this.$emit("delete-todo", item)
                this.$emit("is-disable-delete-btn")
            },
            editTodoDblClick(item){
                this.$emit("edit-todo-dbl-click", item)
            },
            editTextInLi(item){
                this.$emit("edit-exact-todo", item)
            }

        }
    }
</script>

<style scoped>
    .divRemaining{
        margin: 0;
        padding: 0;
        padding-left: 20px;
        padding-right: 20px;
        display: flex;
        justify-content: space-between;
        padding-bottom: 10px;
    }

    .checkboxLabel{
        position: relative;
        cursor: pointer;
    }

    .checkboxLabel{
        position: absolute;
        /*left: 5px;*/
        content: "";
        background-color: #eee0;
        border: 2px solid #aabfb0;
        display: inline-block;
        width: 24px;
        height: 24px;
        border-radius: 50%;
    }

    .checkboxLabel:hover{
        background-color:#e1e8e3;
    }

    .checkboxClass{
        position: absolute;
        left: -9999px;
    }
    .disableDeleteBtn{
        pointer-events: none;
    }

    .disabledCheckbox{
        pointer-events: none;
    }

</style>