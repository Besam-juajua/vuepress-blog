<template>
  <div class="search-container">
	  <div class="search-group">
		  <div class="input-group">
			  <input type="text" placeholder="请输入文章关键字" />
			  <span class="icon">
				  <svg t="1577504379824" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1262" width="100%" height="100%"><path d="M849.340051 799.881616c66.621327-77.68736 106.876146-178.648796 106.876146-289.01544 0-245.333568-198.88263-444.216197-444.216197-444.216197S67.783803 265.531586 67.783803 510.866177s198.88263 444.216197 444.216197 444.216197c110.366643 0 211.32808-40.254819 289.01544-106.876146l96.868211 96.868211c13.343913 13.343913 34.979676 13.343913 48.324612 0s13.343913-34.979676 0-48.324612L849.340051 799.881616zM512.313132 882.035708c-204.817806 0-370.855376-166.037571-370.855376-370.855376s166.037571-370.855376 370.855376-370.855376 370.855376 166.037571 370.855376 370.855376S717.130937 882.035708 512.313132 882.035708z" p-id="1263"></path></svg>
			  </span>
		  </div>
		  <button class="search-btn">搜索文章</button>
	  </div>
      <h1>search</h1>
      <!-- <Content/> -->
  </div>
</template>
<script>
export default {
    name: "Search",
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
	.search-container
		background #fff
	.search-group 
		display flex
		align-items center
		margin 0 4%
		.input-group
			flex 1
			display flex
			align-items center
			height 38px
			padding 0 20px
			box-sizing border-box
			border 1px solid #888888
			border-radius 4px
			input
				flex 1
				height 100%
				border none
				background none
				&:focus
					outline none
			.icon
				display block
				width 22px
				height 22px
		.search-btn
			width 120px
			height 38px
			line-height 38px
			text-align center
			margin-left 10px
			border none
			border-radius 4px
			background #36393c
			color white
			font-size 14px
			
</style>