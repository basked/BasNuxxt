<template>
    <nav-bar class="dxavbar"
            :data-source="navDataStore"
            :selected-index="1",
            :on-item-click="onItemClick"
    >

    </nav-bar>
</template>

<script>
    import DataSource from 'devextreme/data/data_source';
    import {contacts, navData} from '@/store/DevData/NavBar.js';
    import NavBar from 'devextreme-vue/nav-bar';

    export default {
        name: "BasNavBar",
        components: {
            NavBar
        },
        data() {
            return {
                navDataStore: new DataSource(navData)
            }
        },
        methods:{
            onItemClick(e){
                    //list.option("dataSource", listData[e.itemIndex].data);
                console.log(e.itemIndex);
            }
        }

    }
</script>

<style scoped>
    .dxavbar {
        text-align: center;
        position: absolute;
        bottom: 0;
    }
</style>