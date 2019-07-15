<template>
    <div>
        <bas-popup :propsPopupVisible.sync="isPopupVisible" @hidePopup="hidePopup"></bas-popup>
        <dx-toolbar :items="items"/>
        <dx-list
                id="products"
                :data-source="productsStore"
        />
    </div>
</template>
<script>
    import 'devextreme/dist/css/dx.common.css';
    import 'devextreme/dist/css/dx.material.teal.light.compact.css';


    import DxToolbar from 'devextreme-vue/toolbar';
    import DxList from 'devextreme-vue/list';

    import DataSource from 'devextreme/data/data_source';
    import notify from 'devextreme/ui/notify';
    import 'devextreme/ui/select_box';
    import {productTypes, products} from '@/store/DevData/ToolBar.js';
    import BasPopup from '@/components/BasPopup'

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

    #products {
        margin-top: 10px;
    }
</style>
