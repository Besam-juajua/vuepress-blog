<template>
  <div class="slider-container">
      <h1>home</h1>

        
      <Content/>
  </div>
</template>
<script>
export default {
    name: "Home",
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
        clickImage(index) {
            console.log(index)
        }
    }
}
</script>
<style scoped lang="stylus">

    

    // absolute-border()
    //     width 4px
    //     height 4px
    //     position absolute
    //     background red
    //     transition all .5s

    // .border-top
    //     absolute-border()
    //     top 0
    //     left 0
    //     width: 100%
        
    // .border-right
    //     absolute-border()
    //     top 0
    //     right 0
    //     height 100%
    
    // .border-bottom
    //     absolute-border()
    //     left 0
    //     bottom 0
    //     width 100%
    
    // .border-left
    //     absolute-border()
    //     left 0
    //     top 0
    //     height 100%
    
    // .border-hover:hover
    //     width 100%
    //     height 100%
    //     transition all .5s
</style>