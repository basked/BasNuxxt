<template>
    <dx-progress-bar
            id="progress-bar-status"
            :min="0"
            :max="maxValue"
            :value="curValue"
            width="90%"
    />
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
            propsCurValue: Number
        },
        data() {
            return {
                maxValue: this.propsMaxValue,
                curValue: this.propsCurValue
            }
        }
    }
</script>

<style scoped>

</style>