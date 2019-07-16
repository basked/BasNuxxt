<template>
    <div>
        <bas-popup :propsPopupVisible.sync="isPopupVisible" @hidePopup="hidePopup"></bas-popup>
        <dx-toolbar class="dx-toolbar" :items="items"/>
        <dx-list class="dx-list"
        :data-source="productsStore"
        />
    </div>
</template>
<script>
    import 'devextreme/dist/css/dx.common.css';
    import 'devextreme/dist/css/dx.material.orange.light.css';
    import DxToolbar from 'devextreme-vue/toolbar';
    import DxList from 'devextreme-vue/list';
    import notify from 'devextreme/ui/notify';
    import 'devextreme/ui/select_box';
    import BasPopup from '@/components/BasPopup'

    import DataSource from 'devextreme/data/data_source';
    import {productTypes, products} from '@/store/DevData/ToolBar.js';
    export default {
        name: "BasToolBar",
        components: {
            DxToolbar,
            DxList,
            BasPopup
        },
        data() {
            return {
                isPopupVisible: false,
                productsStore: new DataSource(products),
                items: [{
                    location: 'before',
                    widget: 'dxButton',
                    options: {
                        type: 'back',
                        text: 'Back',
                        onClick: (e) => {
                            this.isPopupVisible = true;
                          //  notify('Back button has been clicked!');
                        },
                    }
                }]
            };
        },
        methods: {
             // параметр может быть с любым именем, название функции любое, но совпадать @hidePopup="hidePopup"
            hidePopup(isPopupVisible) {

                this.isPopupVisible = isPopupVisible
            }
        }
    };
</script>
<style>
    .toolbar-label,
    .toolbar-label > b {
        font-size: 16px;
    }
    .dx-toolbar {
        height: 8vh;
        position: absolute;
        top: 0;
        bottom: 0;
    }
    .dx-list {
        height: 82vh;
        position: absolute;
        top: 8%;
        bottom: 0;
    }

</style>
