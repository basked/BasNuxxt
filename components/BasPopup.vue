<template>
    <div id="popup">

        <dx-popup :visible.sync="popupVisible"
                  :drag-enabled="true"
                  :resize-enabled="true"
                  :close-on-outside-click="true"
                  :show-title="true"
                  :width="400"
                  :height="340"
                  :on-showing="onShowing"
                  :on-hiding="onHiding"
                  class="popup"
                  title="Information"
        >
            <dx-scroll-view :height="240">
                <ul>
                    <li>
                        <bas-progress-bar :propsMaxValue="20" :propsCurValue="0" :propsItemId="1"
                                          :propsItemName="'Process #1'"/>
                    </li>
                    <li>
                        <bas-progress-bar :propsMaxValue="20" :propsCurValue="5" :propsItemId="2"
                                          :propsItemName="'Process #2'"/>
                    </li>
                    <li>
                        <bas-progress-bar :propsMaxValue="20" :propsCurValue="10" :propsItemId="3"
                                          :propsItemName="'Process #3'"/>
                    </li>
                    <li>
                        <bas-progress-bar :propsMaxValue="20" :propsCurValue="15" :propsItemId="4"
                                          :propsItemName="'Process #4'"/>
                    </li>


                </ul>
            </dx-scroll-view>
        </dx-popup>
    </div>
</template>

<script>
    import {DxPopup} from 'devextreme-vue/popup';
    import {DxScrollView} from 'devextreme-vue/scroll-view';
    import BasProgressBar from '~/components/BasProgressBar.vue'


    export default {
        name: "BasPopup",
        components: {
            DxPopup,
            DxScrollView,
            BasProgressBar
        },
        props: {propsPopupVisible: Boolean, requre: true},
        data() {
            return {
                curValue: 0,
                inProgress: false,
                popupVisible: false
            }
        },
        watch: {
            propsPopupVisible() {
                this.popupVisible = this.propsPopupVisible;
            }
        },
        methods: {
            onShowing() {

                this.$emit('showPopup', this.popupVisible);
            },
            onHiding() {
                this.$emit('hidePopup', this.popupVisible);
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style-type: none;
        text-align: center;
        background-color: gainsboro;
    }

    ul li {
        display: inline-block;
        width: 100%;
        color: gainsboro;
        background-color:  darkseagreen;
        margin-bottom: 10px;
        font-size: small;
    }


</style>