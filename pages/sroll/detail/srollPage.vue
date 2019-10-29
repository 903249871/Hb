<template>
	<view>
		<view class="content">
			<uni-list >
				<view v-for="list in lists" :key="list">
					<uni-list-item :title="list" thumb="https://img-cdn-qiniu.dcloud.net.cn/new-page/hx.png"></uni-list-item>
				</view>
			</uni-list>
		</view>
		<view v-show="isLoadMore" class="load-more">
			<uni-load-more :status="loadMoreStatus" ></uni-load-more>
		</view>
	</view>
</template>

<script>
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	import uniLoadMore from '@/components/uni-load-more/uni-load-more.vue'
	export default {
		components: {
			uniList,
			uniListItem,
			uniLoadMore
		},
		data() {
			return {
				title: 'Hello'
				,lists: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17]
				,loadMoreText: '加载更多'
				,isLoadMore: false
				,loadMoreStatus: 'more'
			}
		},
		onLoad() {

		},
	    onPullDownRefresh:function(){
			this.upLoadList();
		},
		onReachBottom:function(){
			this.downLoadList()
		},
		methods: {
			upLoadList(){
				for(var i = 0; i<5; i++){
					this.lists.unshift(this.lists[0]-1);
				}
				uni.stopPullDownRefresh();
			},
			downLoadList(){
				this.isLoadMore = true;
				this.loadMoreStatus = "loading";
				if(this.lists.length>50){
					this.loadMoreStatus = "noMore";
				}else{
					setTimeout(()=>{ //模拟请求
						//方法体
						for(var i = 0; i<5; i++){
							this.lists.push(this.lists[this.lists.length-1]+1);
						}
						this.isLoadMore = false;
						//end方法体
					}, 3000);
				}
			}

		}
	}
</script>

<style>
</style>
