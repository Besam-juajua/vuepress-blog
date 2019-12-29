<template>
  <div class="category-container">
        <!-- <bread-crumb :list="navPath" style="padding: 16px 0 30px;"/> -->
        <!-- <div class="main"> -->
            <transition name="bounceUp">
                <section class="tag-group" @click="skip">
                    <div class="img-wrapper" v-for="(item, index) in imagesList" :key="index" @click="clickImage(index)">
                        <div class="img" :style="'backgroundImage: url('+item.img+');'">
                            <img :src="item.img" alt="" srcset="">
                        </div>
                        <div class="info">
                            <span class="size">{{item.text}}</span>
                        </div>
                    </div>
                </section>
            </transition>
            <!-- <transition name="fade">
                <Content style="position: absolute; width: 100%;" v-if="path !== '/category/'"/>
            </transition> -->
        <!-- </div> -->
        
        <!-- <transition name="fadeRight">
            
        </transition> -->
  </div>
</template>
<script>
export default {
    name: "Category",
    props: ["path"],
    data: () => {
        return {
            imagesList: [
                { 
                    img: '/img/1.jpg',
                    text: "Git",
                    link: '/git'
                }, { 
                    img: '/img/2.jpg',
                    text: 'JS/ES6',
                    link: '/js'
                }, { 
                    img: '/img/3.jpg',
                    text: "Vue",
                    link: '/vue'
                }, { 
                    img: '/img/4.jpg',
                    text: "React",
                    link: '/react'
                }, { 
                    img: '/img/5.jpg',
                    text: "Vuex",
                    link: '/vuex'
                }, { 
                    img: '/img/6.jpg',
                    text: "Mobx",
                    link: '/mobx'
                }, { 
                    img: '/img/7.jpg',
                    text: "SSR",
                    link: '/ssr'
                }, { 
                    img: '/img/8.jpg',
                    text: "http",
                    link: '/http'
                }, { 
                    img: '/img/9.jpg',
                    text: "Uniapp",
                    link: '/uniapp'
                }, { 
                    img: '/img/10.jpg',
                    text: "Node.js",
                    link: '/node'
                }

            ]
        }
    },
    beforeMount() {
            
    },
    mounted() {
        console.log("sdjfksdjfklds >> ", this.path)
    },
    destroyed(){

    },
    methods: {
        skip() {
            this.$router.push("/article/git/git基本操作")
        }
    }
}
</script>
<style scoped lang="stylus">
    .category-container
        padding 0 4%
        box-sizing border-box
        background #fff
    .tag-group
        display flex
        flex-wrap wrap
        padding 15px 5px
        box-sizing border-box
        &:after
            content ""
            flex-grow 99999

    .img-wrapper
        flex-grow 1
        margin 5px
        position relative
        overflow hidden
        height 160px
        border 5px solid gray
    
        .img
            background-size cover
            background-position center

            img 
                opacity 0
                min-width 100%
                height 160px

        .tag-name
            position absolute
            left 0
            top 0
            width 100%
            height 100%
            line-height 160px
            text-align center
            font-size 46px
            color #dfdfdf
            background #000
            opacity .4
        .info
            position absolute
            bottom 0px
            color #dfdfdf
            left 0
            right 0
            margin auto
            background-color rgba(0, 0, 0, 0.3)
            line-height 60px
            height 60px
            width 100%
            text-align center
            font-size 32px
      
        &:hover 
            .info
                height 100%
                width 100%
                line-height 160px
                transition all 0.2s ease-out
                color #fff
                font-size 56px
                font-weight bold
</style>