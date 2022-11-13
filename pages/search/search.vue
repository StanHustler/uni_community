<template>
	<view>
		<template v-if="searchList.length === 0">
			<!-- 搜索历史 -->
			<view class="py-2 font-md px-2">搜索历史</view>
			<view class="flex flex-wrap">
				<view class="border rounded font mx-2 my-1 px-2" v-for="(item, index) in list" :key="index"
					hover-class="bg-light" @click="clickSearchHistory(item)">{{ item }}</view>
			</view>
		</template>
		<template v-else>
			<!-- 数据列表 -->
			<block v-for="(item, index) in searchList" :key="index">
				<post :item="item" :index="index"></post>
			</block>
		</template>

	</view>
</template>

<script>
// 测试数据
const demo = [
	{
		username: "qq",
		userpic: "/static/def.png",
		newstime: "2077-01-01",
		isFollow: true,
		title: "我是标题",
		titlepic: "/static/demo/datapic/12.jpg",
		support: {
			type: 0,
			support_count: 2,
			unsupport_count: 2
		},
		comment_count: 2,
		share_num: 2
	}
];
import post from '@/components/post.vue';
export default {
	components: {
		post
	},
	data() {
		return {
			searchText: "",
			list: ['aaa', 'bbb', 'ccc', 'ddd'],
			// 搜索结果
			searchList: []
		}
	},
	// 监听导航输入
	onNavigationBarSearchInputChanged(e) {
		this.searchText = e.text
	},
	// 监听点击导航搜索按钮
	onNavigationBarButtonTap(e) {
		if (e.index === 0) {
			this.searchEvent()
		}
	},
	methods: {
		// 点击搜索历史
		clickSearchHistory(text) {
			this.searchText = text
			this.searchEvent()
		},
		// 搜索事件
		searchEvent() {
			// 收起键盘
			uni.hideKeyboard()
			// 显示loading状态
			uni.showLoading({
				title: '加载中...',
				mask: false
			})
			// 请求搜索
			setTimeout(() => {
				this.searchList = demo
				// 隐藏loading
				uni.hideLoading()
			}, 1500)
		}
	}
}
</script>

<style>

</style>