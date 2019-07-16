<template>
    <div id="popup">

        <dx-popup :visible.sync="popupVisible"
                  :drag-enabled="true"
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
                        <bas-progress-bar :propsMaxValue="20"  :propsCurValue="10"  :propsItemId="1" :propsItemName="'Nu10'" />
                    </li>
                    <!--<li>-->
                        <!--<bas-progress-bar :propsMaxValue="70" :propsName='Val 20' :propsCurValue="20"/>-->
                    <!--</li>-->
                    <!--<li>-->
                        <!--<bas-progress-bar :propsMaxValue="70" :propsName='Val 30' :propsCurValue="30"/>-->
                    <!--</li>-->
                    <!--<li>-->
                        <!--<bas-progress-bar :propsMaxValue="70" :propsName='Val 40' :propsCurValue="40"/>-->
                    <!--</li>-->
                    <!--<li>-->
                        <!--<bas-progress-bar :propsMaxValue="70" :propsName='Val 50' :propsCurValue="50"/>-->
                    <!--</li>-->
                    <!--<li>-->
                        <!--<bas-progress-bar :propsMaxValue="70" :propsName='Val 60' :propsCurValue="60"/>-->
                    <!--</li>-->

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
        background-color: palegreen;
        margin-bottom: 10px;
        font-size: small;
    }


</style>