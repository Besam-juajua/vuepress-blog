<template>
    <div class="layout">
        <transition name="fade">
            <div class="top-border" v-if="toMove"></div>
        </transition>
        <div class="theme-container">
            <transition name="fade">
                <header class="theme-slider main-box" v-if="toMove">
                    <slider :path="pathname"/>
                </header>
            </transition>
            <section class="content shadow-box">
                <bread-crumb :list="navPath" style="padding: 16px 0 30px;"/>
                <transition name="bounceUp">
                    <home :path="fullPath" v-if="pathname === '/home/'" class="absolute"/>
                </transition>
                <transition name="bounceUp">
                    <category :path="fullPath" v-if="pathname === '/category/'" class="absolute"/>
                </transition>
                <transition name="bounceUp">
                    <perfect :path="fullPath" v-if="pathname === '/perfect/'" class="absolute"/>
                </transition>
                <transition name="bounceUp">
                    <search :path="fullPath" v-if="pathname === '/search/'" class="absolute"/>
                </transition>
                <transition name="bounceUp">
                    <interaction :path="fullPath" v-if="pathname === '/interaction/'" class="absolute"/>
                </transition>
                <transition name="lightSpeed">
                    <besam v-if="pathname === '/besam/'"/>
                </transition>
                <transition name="lightSpeed">
                    <Content v-if="toMove"/>
                </transition>
            </section>
            
        </div>
        <footer class="theme-footer">
                
        </footer>
    </div>
</template>
<script>
export default {
    name: "Layout",
    data: () => {
        return {
            toMove: true,
            fullPath: "",
            pathname: "",
            navPath: [{
                text: "首页",
                link: "/home"
            }],
            navMapping: {
                home: "首页",
                category: "分类",
                perfect: "精选",
                search: "搜索",
                interaction: "答疑互动"
            }
        }
    },
    mounted() {
        this.toMove = false
        // this.toMove = true
        setTimeout(() => {
            this.toMove = true
        }, 0)
        this.pathname = location.pathname.replace("/blog", "");
        this.fullPath = location.pathname.replace("/blog", "");
    },
    methods: {

    },
    watch: {
        $route(to,from){
            let path = to.path;
            this.fullPath = path;
            this.pathname = /^\/home\/.*/.test(path) ? "/home/" :
                            /^\/category\/.*/.test(path) ? "/category/" :
                            /^\/perfect\/.*/.test(path) ? "/perfect/" :
                            /^\/search\/.*/.test(path) ? "/search/" :
                            /^\/interaction\/.*/.test(path) ? "/interaction/" :
                            /^\/besam\/.*/.test(path) ?  "/besam/" : ""
        },
        fullPath(path) {
            console.log("111111")
            let mapping = this.navMapping;
            let list = path.split("/");
            list.shift();
            list.pop();
            let baseNav = "";
            let tempList = [];
            list.forEach((val, index) => {
                baseNav += baseNav + '/';
                if(index === 0) {
                    console.log("fff >> ", val)
                    if(!mapping[val]) {
                        console.log("999999")
                        tempList[0] = this.navPath[0];
                        return;
                    };
                    console.log("list ", list)
                    tempList[0] = {
                        text: mapping[val],
                        link: baseNav + val
                    }
                } else {
                    tempList[index] = {
                        text: val,
                        link: baseNav + val
                    }
                }
            })
            this.navPath = tempList;
            console.log("22222")
        }
    }
}
</script>
<style scoped lang="stylus">
    .top-border
        width 100%
        height 2px
        background-color #1d1f21
    .theme-container
        width 80%
        max-width 1420px
        min-width 768px
        margin 0 auto
        display flex
        position relative
        
    .shadow-box
        // box-shadow 0 2px 2px 0 rgba(0,0,0,.12), 0 3px 1px -2px rgba(0,0,0,.06), 0 1px 5px 0 rgba(0,0,0,.12), 0 -1px 0.5px 0 rgba(0,0,0,.09)

    .theme-slider
        width calc(24% - 10px)
        max-width 266px
        margin-right 10px
    
    .content
        position absolute
        left 24%
        width 76%
        padding 20px 36px
        box-sizing border-box
        // background #fff
    
        .absolute
            position absolute;
            width 100%;


    @media screen and (min-width 1450px)
        .content
            width calc(100% - 276px)
            left 276px
    
    @media screen and (max-width 768px) 
        .theme-container 
            width 96%
            margin 0 auto
        
        .theme-slider 
            display none
        
    

</style>