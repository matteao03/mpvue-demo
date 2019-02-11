<template>
	<div class="index">
		<div class="header-r" @click="searchClick">
			<van-icon name="search" size="15px"/>
			<span class="search-text">搜索文章、帖子...</span>
		</div>
		
	</div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  methods: {
    searchClick () {
      wx.navigateTo({url: '../searchList/main'})
    }
  },

  created () {

  }
}
</script>

<style lang="scss" scoped>
	.header-r {
		display: flex;
		align-items: center;
		flex: 1;
		background-color: $page-bgcolor;
		height: 30px;
		border-radius: 15px;
		margin:0 15px;
		padding-left:10px;
		align-items: center;
		
		.search-text {
			color: $textDarkGray-color;
			font-size: 12px;
			margin-left: 12px;
		}
	}
	
</style>
