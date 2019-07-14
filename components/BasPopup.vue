<template>
    <div id="popup">
        <h1>Employees</h1>

        <ul>
            <li>basked1</li>
            <li>basked2</li>
            <li>basked3</li>
            <li>basked4</li>
            <li>basked5</li>
        </ul>
        <dx-popup :visible.sync="popupVisible"
                  :drag-enabled="false"
                  :close-on-outside-click="true"
                  :show-title="true"
                  :width="300"
                  :height="250"
                  class="popup"
                  title="Information"
        >
        </dx-popup>
    </div>
</template>

<script>
    import {DxPopup} from 'devextreme-vue/popup';

    export default {
        name: "BasPopup",
        components: {
            DxPopup
        },
        props: {
            propsPopupVisible: Boolean
        },
        data() {
            return {
                popupVisible:false
            }
        },

        watch: {
            propsPopupVisible: function (newVal, oldVal) { // watch it

              console.log(  this.popupVisible);
              console.log(newVal);
              console.log( oldVal);
            }
        }
    }
</script>

<style scoped>
    #popup {
        padding: 10px;
    }

    #popup ul {
        list-style-type: none;
        text-align: center;
    }

    #popup ul li {
        display: inline-block;
        width: 160px;
        margin: 10px;
    }

    #popup ul li img {
        width: 100px;
    }

    .button-info {
        margin: 10px;
    }

    .popup p {
        margin-bottom: 10px;
        margin-top: 0;
    }
</style>