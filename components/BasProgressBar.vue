<template>
    <div id="BasProgressBar">
    <p>{{itemName}}[{{itemId}}]: {{curValue}} из {{maxValue}}</p>
    <dx-progress-bar
            id="progress-bar-status"
            :min="0"
            :max="maxValue"
            :value="curValue"
            width="90%"
            :on-initialized="init"
            :on-complete="complete"

    />
    </div>
</template>

<script>
    import {DxProgressBar} from 'devextreme-vue/progress-bar';


    export default {
        name: "BasProgressBar",
        components: {
            DxProgressBar
        },
        props: {
            propsMaxValue: Number,
            propsItemId: Number,
            propsItemName: String,
            propsCurValue: Number

        },
        data() {
            return {
                itemId: this.propsItemId,
                itemName: this.propsItemName,
                maxValue: this.propsMaxValue,
                curValue: this.propsCurValue
            }
        },
        methods: {
            init() {
                console.log('init');
                this.intervalId = setInterval(() => this.timer(), 1000);
            },
            complete(){
               console.log( 'Complete progress '+ this.itemName+'['+this.itemId+']');
            },
            timer() {
                if (this.curValue < this.maxValue) {
                    this.curValue = this.curValue + 1;
                    console.log(this.curValue);
                }
            },
        }
    }
</script>

<style scoped>
    #BasProgressBar>p{
        color: white;
    }
</style>