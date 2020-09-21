<template>
    <div>
        <div class="div-count">
            <div class="line-through-count"
                 v-bind:class=" { lineThroughShow: isLineThroughShow } "
                 v-if="lineThroughCountCalc"
            >
            </div>
                <div class="count"
                     v-if="countCalc">
                    {{completedTodos.length}} / {{remainingTodos.length}}
                    (<span
                        v-bind:class="colourCalc"
                    >
                    {{percentageCalcColor}}
                    </span>% done)
                </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "todoPercentageDone",

        props: {
            remainingTodos: {
                type: Array,
                required: false
            },
            completedTodos: {
                type: Array,
                required: false
            },
            percentageCalcColor: {
                type: Number,
                required: false
            },
            isLineThroughShow: {
                type: Boolean,
                required: true
            },
        },

        computed:{
            lineThroughCountCalc() {
                return this.remainingTodos.length !== 0 || this.completedTodos.length !== 0
            },

            countCalc(){
                return this.remainingTodos.length !== 0 || this.completedTodos.length !== 0
            },
            colourCalc(){
                return `${this.percentageCalcColor === 0 ? 'percentageBlack' :
                        this.percentageCalcColor === 100 ? 'percentageGreen' :
                        this.percentageCalcColor >= 50 ? 'percentageOrange' :
                            this.percentageCalcColor < 50 ? 'percentageRed' : 'percentageBlack'}`
            }
        }

    }
</script>

<style scoped>
    .div-count{
        display: flex;
        padding-bottom: 15px;

    }

    .line-through-count{
        flex-grow: 1;
        border-bottom: 1px solid #ebeae8;
        margin-bottom: 10px;
        margin-right: 10px;
    }

    .lineThroughShow{
        border-bottom: 1px solid #eee0;
    }

    .percentageGreen{
        color: green;
    }

    .percentageOrange{
        color: orange;
    }

    .percentageRed{
        color: red;
    }

    .percentageBlack{
        color: black;
    }

</style>