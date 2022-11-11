<template>
	<view>
		
		<block v-for="(item,index) in posts">
			<post :item="item" :index="index"></post>
			<divider></divider>
		</block>
					
	</view>
</template>

<script>
	import post from "@/components/post.vue"
	import divider from "@/components/divider.vue"
	
	export default {
		components:{
			post,
			divider
		},
		data() {
			return {
				posts: [
					{
						username:"qq",
						userpic:"/static/def.png",
						newstime:"2077-01-01",
						isFollow:true,
						title:"我是标题",
						titlepic:"/static/demo/datapic/12.jpg",
						support:{
							type:"support",
							support_count:1,
							unsupport_count:2
						},
						comment_count:2,
						share_num:2
					},
					{
						username:"ww",
						userpic:"/static/def.png",
						newstime:"2077-01-01",
						isFollow:false,
						title:"我是标题",
						titlepic:"/static/demo/datapic/16.jpg",
						support:{
							type:"support",
							support_count:1,
							unsupport_count:2
						},
						comment_count:2,
						share_num:2
					},
				]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
		background-color: bisque;
	}
</style>
