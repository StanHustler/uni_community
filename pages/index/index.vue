<template>
	<view>
		
		<block v-for="(item,index) in posts">
			<post :item="item" :index="index" @follow="follow" @doSupport="doSupport"></post>
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
							type:0,
							support_count:2,
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
							type:1,
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
			follow(e){
				this.posts[e].isFollow= true;
			},
			doSupport(e){
				let t = this.posts[e.index].support
				if (e.type != t.type){
					if (t.type != null){
						t.type==1 ? t.support_count-- : t.unsupport_count--;
					}
					t.type = e.type
					t.type==1 ? t.support_count++ : t.unsupport_count++;
				}else{
					t.type==1?t.support_count-- : t.unsupport_count--;
					t.type=null;
				}
			}
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
