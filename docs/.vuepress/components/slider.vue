<template>
  <div class="slider-container">
      <transition name="fadeLeft">
            <div class="top-box">
                <h2 class="title">Besam #博客</h2>
                <p class="saying">编程是门技术，更是一门艺术</p>
            </div>
        </transition>
      
      <div class="nav-group" :class="{'fixed-nav': fixedNav}">
          <transition name="fadeDownBig">
            <div class="nav-box shadow-box" v-if="toMove">
                <ul class="nav-list">
                    <li v-for="(item, index) in navList" :class="{'active': path === item.link}">
                        <router-link :to="item.link" tag="a" v-if="item.type === 'innerLink'">
                            <i class="icon" v-html="item.icon"></i>
                            <span>{{item.text}}</span>
                        </router-link>
                        <a :href="item.link" target="_blank" v-else>
                            <i class="icon" v-html="item.icon"></i>
                            <span>{{item.text}}</span>
                        </a>
                    </li>
                </ul>
            </div>
          </transition>
          <transition name="fadeDown">
            <div class="profile-box shadow-box" v-if="toMove">
                <h3 class="catalog">文章目录</h3>
            </div>
        </transition>
      </div>
      
  </div>
</template>
<script>
export default {
    name: "Slider",
    props: ["path"],
    data: () => {
        return {
            navList: [],
            fixedNav: false,
            toMove: true,
        }
    },
    beforeMount() {
        window.addEventListener('scroll', this.getScroll);
        this.navList = [
            {
                icon: '<svg t="1577166393711" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1517" width="16" height="16"><path d="M512 341.333333L170.666667 512v455.111111h398.222222v-227.555555h113.777778v227.555555h170.666666V512L512 341.333333z" fill="#585858" p-id="1518"></path><path d="M910.222222 306.631111V113.777778h-113.777778v129.706666L512 85.333333l-512 284.444445L51.2 455.111111 512 204.8l460.8 256 51.2-91.022222-113.777778-63.146667z" fill="#585858" p-id="1519"></path></svg>',
                text: "首页",
                link: "/home/",
                type: "innerLink"
            }, {
                icon: '<svg t="1577166411988" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1794" width="16" height="16"><path d="M64.003709 181.806719l109.455901 0 0 109.455901-109.455901 0 0-109.455901Z" fill="#555555" p-id="1795"></path><path d="M611.282191 291.26262 282.914488 291.26262 282.914488 181.806719 611.282191 181.806719 647.76715 236.534158Z" fill="#555555" p-id="1796"></path><path d="M793.70801 564.900837 282.914488 564.900837 282.914488 455.44596 793.70801 455.44596 830.192969 510.173398Z" fill="#555555" p-id="1797"></path><path d="M921.40639 838.540078 282.914488 838.540078 282.914488 729.0852 921.40639 729.0852 957.89135 783.812639Z" fill="#555555" p-id="1798"></path><path d="M64.003709 455.44596l109.455901 0 0 109.455901-109.455901 0 0-109.455901Z" fill="#555555" p-id="1799"></path><path d="M64.003709 729.0852l109.455901 0 0 109.455901-109.455901 0 0-109.455901Z" fill="#555555" p-id="1800"></path></svg>',
                text: "分类",
                link: "/category/",
                type: "innerLink"
            }, {
                icon: '<svg t="1577166427218" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1931" width="16" height="16"><path d="M929.5 409.1c20.5-20 9.2-54.8-19.2-58.9l-235.9-34.3c-11.3-1.6-21-8.7-26-18.9L543 83.2c-12.7-25.7-49.3-25.7-62 0L375.5 297c-5 10.2-14.8 17.3-26 18.9l-235.9 34.3c-28.3 4.1-39.7 38.9-19.2 58.9l170.7 166.4c8.1 7.9 11.9 19.4 9.9 30.6L234.8 841c-4.8 28.2 24.8 49.8 50.1 36.4l211-110.9c10.1-5.3 22.1-5.3 32.2 0l211 110.9c25.3 13.3 55-8.2 50.1-36.4l-40.3-235c-1.9-11.2 1.8-22.6 9.9-30.6l170.7-166.3z" fill="#555555" p-id="1932"></path></svg>',
                text: "精选",
                link: "/perfect/",
                type: "innerLink"
            }, {
                icon: '<svg t="1577164779146" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1244" width="16" height="16"><path d="M824.612571 0c40.886857 0 73.581714 33.353143 74.203429 73.654857v437.540572l-317.513143-1.024a87.771429 87.771429 0 0 0-88.027428 86.601142l-5.12 387.84H128.438857C88.210286 984.612571 54.857143 951.881143 54.857143 910.994286V73.654857C54.857143 33.353143 87.552 0 128.438857 0h696.173714z m-108.8 409.380571c0-21.101714-16.457143-39.021714-36.059428-39.021714H232.228571c-19.602286 0-36.059429 17.261714-36.059428 39.021714 0 21.101714 16.457143 39.021714 36.059428 39.021715h447.561143c20.224 0 36.059429-17.261714 36.059429-39.021715zM231.497143 518.180571c-19.565714 0-36.022857 17.261714-36.022857 39.021715 0 21.138286 16.457143 39.058286 36.022857 39.058285h176.384c19.602286 0 36.059429-17.298286 36.059428-39.058285 0-21.101714-16.457143-39.021714-36.059428-39.021715H231.533714z m0.658286-229.12h447.561142c19.602286 0 36.059429-17.261714 36.059429-39.021714 0-21.138286-16.457143-39.058286-36.059429-39.058286H232.228571c-19.602286 0-36.059429 17.298286-36.059428 39.058286 0 21.76 16.457143 39.021714 36.059428 39.021714z" fill="#555555" p-id="1245"></path><path d="M920.612571 896.475429l33.901715 33.901714a47.067429 47.067429 0 0 1 0 68.205714 47.067429 47.067429 0 0 1-68.169143 0l-40.045714-40.045714a226.523429 226.523429 0 0 1-105.728 26.075428c-125.732571 0-228.571429-102.838857-228.571429-228.571428 0-125.696 102.875429-228.571429 228.571429-228.571429 125.732571 0 228.571429 102.875429 228.571428 228.571429a227.218286 227.218286 0 0 1-48.530286 140.434286z m-181.394285-284.598858a141.458286 141.458286 0 0 0-142.811429 142.848 141.458286 141.458286 0 0 0 142.848 142.848 141.458286 141.458286 0 0 0 142.848-142.848 141.458286 141.458286 0 0 0-142.848-142.848z" fill="#555555" p-id="1246"></path></svg>',
                text: "搜索",
                link: "/search/",
                type: "innerLink"
            }, {
                icon: '<svg t="1577174505841" class="icon" viewBox="0 0 1137 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="945" width="16" height="16"><path d="M242.66666656 192.00000031L245.33333375 676.53333312h429.70666594L743.89333344 778.66666625H458.66666656l-133.33333312 213.33333375L192.00000031 778.66666625H32V192.00000031h210.66666656z" fill="#555555" p-id="946"></path><path d="M992 618.66666688l-133.33333312 213.33333281-133.33333313-213.33333281H298.66666625V32h800.00000062v586.66666688h-106.66666687z m-266.66666625-266.66666719a53.33333344 53.33333344 0 1 0 0-106.66666594 53.33333344 53.33333344 0 0 0 0 106.66666594z m213.33333281 0a53.33333344 53.33333344 0 1 0 0-106.66666594 53.33333344 53.33333344 0 0 0 0 106.66666594zM512 351.99999969a53.33333344 53.33333344 0 1 0 0-106.66666594 53.33333344 53.33333344 0 0 0 0 106.66666594z" fill="#555555" p-id="947"></path></svg>',
                text: "答疑互动",
                link: "/interaction/",
                type: "innerLink"
            }, {
                icon: '<svg t="1577166442422" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2063" width="16" height="16"><path d="M500.5 731.9L395.2 536.2c-7-12.9 2.4-28.6 17.1-28.6H623c14.7 0 24.1 15.7 17.1 28.6L534.8 731.9c-7.4 13.6-26.9 13.6-34.3 0z" fill="#707070" p-id="2064"></path><path d="M517.6 87.4c-104.9 0-189.9 85-189.9 189.9s85 189.9 189.9 189.9 189.9-85 189.9-189.9S622.6 87.4 517.6 87.4z m0 319.6C444.9 407 386 349.9 386 277.3s59-131.6 131.6-131.6 131.6 58.9 131.6 131.6S590.3 407 517.6 407z" fill="#555555" p-id="2065"></path><path d="M645.4 465.2H389.5c-104.5 0-190.1 85.5-190.1 190.1v291.5c0 17.1 14 31.1 31.1 31.1h575c16.7 0 30.4-13.7 30.4-30.4V655.7c0-104.8-85.7-190.5-190.5-190.5z m117.9 415.4c0 12.4-10.2 22.6-22.6 22.6H300.1c-12.7 0-23.2-10.4-23.2-23.2V654c0-67.7 55.4-123 123-123h246c64.5 0 117.3 52.8 117.3 117.3v232.3z" fill="#555555" p-id="2066"></path></svg>',
                text: "Besam",
                link: "http://besam-juajua.github.io",
                type: "outLink"
            }
        ]
            
    },
    mounted() {
        this.toMove = false;
        // this.toMove = true;
        setTimeout(() => {
            this.toMove = true
        }, 0)
        console.log(" >>>> ", this.path)
    },
    destroyed(){
        window.removeEventListener('scroll', this.getScroll);
    },
    methods: {
        getScroll(e) {
            let top = document.documentElement.scrollTop;
            this.fixedNav = (top > 100)
        }
    }
}
</script>
<style scoped lang="stylus">
    *
        margin 0
        padding 0
    .top-box
        width 100%
        height 98px
        text-align center
        background-color #1d1f21
        .title
            padding 20px 0 8px
            border none
            font-size 22px
            color white;
        .saying
            font-size 14px
            color #eee
    .nav-group
        width 100%
        .nav-box
            padding 20px 0 16px
            background-color rgba(255, 255, 255, .46)
            box-sizing border-box
            .nav-list
                list-style none
                li
                    height 40px
                    line-height 40px
                    margin 0 30px
                    a
                        display flex
                        align-item center
                        width 100%
                        height 100%
                        font-size 14px
                        color #555555
                        span 
                            line-height 34px
                            margin-left 12px
                li.active
                    a
                        color #fc6423

        .profile-box
            height 200px
            margin-top 10px
            background-color rgba(255, 255, 255, .46)
            .catalog
                padding 10px 16px
                font-size 18px

    .fixed-nav
        position fixed
        top 0
        width calc(19.2% - 10px)
        max-width 266px
        min-width 174px

    .shadow-box
        box-shadow 0 2px 2px 0 rgba(0,0,0,.12), 0 3px 1px -2px rgba(0,0,0,.06), 0 1px 5px 0 rgba(0,0,0,.12), 0 -1px 0.5px 0 rgba(0,0,0,.09)
    
    .icon
        color blue
</style>