<template>
	<div class="search-list">
		<van-search 
      class="search"
      :value="value" 
      placeholder="搜索文章..." 
      use-action-slot 
      focus 
      @change="onChange"
    >
			<view slot="action" @click="onSearch">搜索</view>
		</van-search>

    <div class="hot">热门搜索</div>
    <div class="hot-line"></div>
    <div class="tag-list">
        <div class="tag" v-for="(item, index) in hotList" :key="index">
          <span>{{item.label_name}}</span>
        </div>
    </div>
    <div class="line-m"></div>
    <div class="history">
      <div class="header">
        <span>历史搜索</span>
      </div>
      <div class="line-b"></div>
      <div class="history-list">
        <div class="item" v-for="(item, index) in historyList" :key="index">
          <span>{{item}}</span>
        </div>
      </div>
    </div>
	</div>
</template>

<script>
import {searchData} from './data'

export default {
  data () {
    return {
      hotList: [],
      historyList: ['麻辣烫', '麦当劳', '小炒肉', '奶茶']
    }
  },
  mounted: function () {
    this.hotList = searchData.data.data.labels
  },
  methods: {
    onSearch () {
      console.log(this.value)
    },
    onChange (event) { // 官方埋得一个坑
      this.value = event.mp.detail
    }
  }
}
</script>

<style lang="scss" scoped>
.search-list{
  .search{
    width:100%;
  }
  .hot{
    margin:15px;
    font-size:12px;
  }
  .hot-line{
    height:1px;
    background-color: $spLine-color;
    margin-left:15px;
  }
  .tag-list {
      display: flex;
      margin: 15px;
      flex-wrap: wrap;
      margin-bottom: 0;
      .tag {
        width: 60px;
        height: 25px;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid $spLine-color;
        margin-right: 10px;
        margin-bottom: 10px;
        span {
          font-size: 10px;
          color: $textBlack-color;
        }
      }
    }
    .line-m {
      height: 10px;
      background-color: $page-bgcolor;
    }

    .history{
      display: flex;
      background-color: white;
      flex-direction: column;
      .header {
        display: flex;
        align-items: center;
        padding: 20rpx 30rpx;
        span {
          display: flex;
          flex: 1;
          font-size: 24rpx;
          color: $textDarkGray-color;
        }
        i {
          font-size: 32rpx;
          color: $textDarkGray-color;
        }
      }
      .line-b {
        height: 1px;
        background-color: $spLine-color;
        margin-left: 15px;
      }
      .history-list {
        display: flex;
        background-color: white;
        margin: 30rpx;
        flex-wrap: wrap;
        margin-bottom: 0;
        .item {
          width: 120rpx;
          height: 50rpx;
          display: flex;
          align-items: center;
          justify-content: center;
          border: 2rpx solid $spLine-color;
          margin-right: 20rpx;
          margin-bottom: 20rpx;
          span {
            font-size: 20rpx;
            color: $textBlack-color;
          }
        }
      }
    }
}
</style>
