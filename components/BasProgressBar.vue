<template>

    <div id="BasProgressBar">
        <p>{{itemName}}[{{itemId}}]: {{curValue}} из {{maxValue}}</p>
        <div class="content">
            <dx-progress-bar
                    id="progress-bar-status"
                    :min="0"
                    :max="maxValue"
                    :value="curValue"
                    :on-initialized="initialized"
                    :on-complete="complete"
                    width="90%"
            />
            <div class="dx-field">
                <div class="dx-field-value">
                    <dx-button
                            class="send"
                            icon="fa fa-retweet"
                            @click="sendClick()"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {DxProgressBar} from 'devextreme-vue/progress-bar';
    import {DxButton} from 'devextreme-vue/button';
    export default {
        name: "BasProgressBar",
        components: {
            DxProgressBar,
            DxButton
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
            initialized() {
                console.log('init');
                this.intervalId = setInterval(() => this.timer(), 1000);
            },
            complete() {
                console.log('Complete progress ' + this.itemName + '[' + this.itemId + ']');
            },
            timer() {
                if (this.curValue < this.maxValue) {
                    this.curValue = this.curValue + 1;
                    console.log(this.curValue);
                }
            },
            sendClick(){
                console.log('Update for '+this.itemName +' id='+this.itemName)
                this.curValue=0;
                this.initialized();

            }
        }
    }
</script>

<style scoped>
    #BasProgressBar > p {
        color: white;
    }
    .content {
        display: flex;
    }
    .dx-field{
        margin-top: -14px;
        margin-left: 20px;
    }
</style>