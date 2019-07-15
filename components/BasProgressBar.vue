<template>
    <div id="BasProgressBar">
    <p>{{curValue}} из {{maxValue}}</p>
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
            propsName:String,
            propsMaxValue: Number,
            propsCurValue: Number

        },
        data() {
            return {
                name: this.propsName,
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
              console.log( 'Complete progress '+ this.name);
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