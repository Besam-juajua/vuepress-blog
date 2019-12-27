<template>
    <div class="bread-crumb">
        <span style="display: inline-block; width: 8px; height: 24px; background: #393939; opacity: .7; margin-right: 8px;"></span>
        <router-link class="crumb-href" v-for="(item, index) in list" :to="item.link" v-if="index + 1 !== list.length">{{item.text}}<span class="crumb-common">&nbsp;&gt;&nbsp;</span></router-link>
        <span class="crumb-common" v-else>{{list[list.length - 1].text}}</span>
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
    .bread-crumb
        display flex
        align-items center
        font-size 15px
        .crumb-href
            font-weight bold
            color #393939
            &:hover
                color #fc6423
        .crumb-common
            color gray
            &:hover
                color gray
    
</style>