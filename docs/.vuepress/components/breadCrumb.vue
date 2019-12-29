<template>
    <div class="bread-container">
        <div class="bread-crumb">
            <span style="display: inline-block; width: 8px; height: 18px; background: #a3a3a3; opacity: .7; margin-right: 8px;"></span>
            <router-link class="crumb-href" v-for="(item, index) in list" :to="item.link" v-if="index + 1 !== list.length">{{item.text}}<span class="crumb-common">&nbsp;/&nbsp;</span></router-link>
            <span class="crumb-common" v-else>{{list[list.length - 1].text}}</span>
        </div>
    </div>
</template>
<script>
export default {
    name: "Category",
    props: {
        list: {
            type: Array,
            default: [],
        }
    },
    data: () => {
        return {
        }
    },
    beforeMount() {
            
    },
    mounted() {

    },
    destroyed(){

    },
    methods: {

    }
}
</script>
<style scoped lang="stylus">
    .bread-container
        display inline-block
    .bread-crumb
        display flex
        align-items center
        font-size 13px
        padding 10px 60px 4px 0
        box-sizing border-box
        border-bottom 1px solid #e1e3e5
        .crumb-href
            color #a3a3a3
            &:hover
                color #fc6423
        .crumb-common
            color #a3a3a3
            &:hover
                color #a3a3a3
    
</style>