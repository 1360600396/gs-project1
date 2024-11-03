<template>
  <div style="width: 100%; height: 100%; overflow: hidden;">
    <!-- <iframe :src="url" style="width: 100%; height: 100%; border: 0px;"></iframe> -->
<div class="banma-warp">
	<div class="condition-box">
			<div class="title-box">
				<div 
					v-for="(item, index) in titles" 
					:key="index"	
					:class="current == index ? 'active' : ''"
					@click="changeTitle(item, index)"
				>
				<div class="title-box1">
					<span class="title-boxfont1">{{ item.title }}</span>
					<span class="title-boxfont2"> {{ item.subTitle }} </span>
				</div>
				<img :src=item.src alt="">
				</div>
			</div>
			<div class="search">
        <input type="text" placeholder="请输入课程名称" v-model="value">
        <a href="#" @click="search()"></a>
      </div>

		</div>
		<div class="list-box" v-if="current==0">
			<div  class="list-item" v-for="(item, index) in searchResults" :key="index" @click="fn(item)">
				<div class="list-item-box">
					<div class="tips">{{ item.tips }}</div>
					<!-- <img v-lazy="imgUrl" alt=""> -->
           <!-- <img src="../assets/广联达斑马进度计划软件2020教学视频（详细功能教学合集，分9部分） (3).png" alt=""> -->
		   <img :src=item.srcimg alt="" width="214.4px" height="150px">
		   <!-- <img src="../assets/banner1/新-教学视频小节封面_04.png" alt=""> -->
					<div class="list-desc">
						<div class="title">{{ item.title }}</div>
						<div class="time">{{ item.time }}</div>
					</div>
				</div>
				
			</div>
		</div>
		<div class="list-box" v-if="current==1">
			<div  class="list-item" v-for="(item, index) in searchResults" :key="index" @click="fn(item)">
				<div class="list-item-box">
					<div class="tips">{{ item.tips }}</div>
					<!-- <img v-lazy="imgUrl" alt=""> -->
           <!-- <img src="../assets/广联达斑马进度计划软件2020教学视频（详细功能教学合集，分9部分） (3).png" alt=""> -->
		   <img :src=item.srcimg alt="">
		  
					<div class="list-desc">
						<div class="title">{{ item.title }}</div>
						<div class="time">{{ item.time }}</div>
					</div>
				</div>
				
			</div>
		</div>
		<div class="list-box" v-if="current==2">
			<div  class="list-item" v-for="(item, index) in searchResults" :key="index" @click="fn(item)">
				<div class="list-item-box">
					<div class="tips">{{ item.tips }}</div>
					<!-- <img v-lazy="imgUrl" alt=""> -->
           <!-- <img src="../assets/广联达斑马进度计划软件2020教学视频（详细功能教学合集，分9部分） (3).png" alt=""> -->
		   <img :src=item.srcimg alt="">
					<div class="list-desc">
						<div class="title">{{ item.title }}</div>
						<div class="time">{{ item.time }}</div>
					</div>
				</div>
				
			</div>
		</div>
		
</div>


  </div>
  
</template>

<script>
	import { Input } from 'ant-design-vue';
export default {
  name: "ClientGuideIframe",
  data() {
	  return {
		searchResults: [],
				imgUrl: "https://build.glodonedu.com/oss/image/byid/3574132519423513066",
				titles: [
					{id: 1, title: "软件学习", subTitle: "技能充电宝",src:require('@/assets/wrap/软件学习@1x.png')},
					{id: 2, title: "专家课堂", subTitle: "职场加速器",src:require('@/assets/wrap/专家课堂@1x.png')},
					{id: 3, title: "直播回顾", subTitle: "精彩不打烊",src:require('@/assets/wrap/直播回顾@1x.png')},
					{id: 4, title: "全部视频", subTitle: "精彩不打烊",src:require('@/assets/wrap/全部视频@1x.png')}
				],
				current: 0,
				value: "", // 搜索框的值
			
				pics: [
					{
						id: 1, title: "1.1斑马进度计划产品介绍", tips: "软件学习", time: "05:03", src: 'https://jzkt.fwxgx.com/courses/24304/videos/157977/play',
						srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 2, title: "1.2网络图基础知识", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/157705/play',
						srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 3, title: "1.3斑马进度计划界面介绍", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154346/play'
						,srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 4, title: "2.1新建与保存计划文件", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154489/play'
						,srcimg:require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 5, title: "2.2如何找回备份文件", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154490/play'
						,srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 6, title: "3.1如何打开黑白模式", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154492/play'
						,srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 7, title: "3.2如何设置护眼模式", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154493/play'
						,srcimg: require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 8, title: "3.3多文件之间如何切换", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154494/play'
						,srcimg:require('@/assets/banner1/新-教学视频小节封面_02.png')
					},
					{
						id: 9, title: "4.1如何添加休息日", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154496/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_09.png'
					},
					{
						id: 10, title: "4.2如何绘制常规工作", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154497/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_10.png'
					},
					{
						id: 11, title: "4.3如何绘制穿插工作", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154498/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_11.png'
					},
					{
						id: 12, title: "4.4如何连接和断开工作", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154499/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_12.png'
					},
					{
						id: 13, title: "4.5如何设置父子结构", tips: "软件学习", time: "", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154500/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_13.png'
					},
					{
						id: 14, title: "4.6如何添加里程碑以及设置里程碑预警", tips: "软件学习", time: "时长：1分钟", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154501/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_14.png'
					},
					{
						id: 15, title: "4.7如何快速复制工作", tips: "软件学习", time: "时长：38秒", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154502/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_15.png'
					},
					{
						id: 16, title: "4.8如何设置分区", tips: "软件学习", time: "时长：35秒", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154503/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_16.png'
					},
					{
						id: 17, title: "4.9如何添加图片和文字标注", tips: "软件学习", time: "时长：44秒", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154504/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_17.png'
					},
					{
						id: 18, title: "4.10快速优化图幅展示", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154505/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_18.png'
					},
					{
						id: 19, title: "6.1如何快速形成周计划、月计划", tips: "", time: "时长：56秒", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154822/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_19.png'
					},
					{
						id: 20, title: "6.2前锋线基础原理讲解", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154823/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_20.png'
					},
					{
						id: 21, title: "7.1工期固定资源均衡", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154824/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_21.png'
					},
					{
						id: 22, title: "7.2资源限量工期最短", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154825/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_22.png'
					},
					{
						id: 23, title: "8.1如何导出图片", tips: "", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154507/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_23.png'
					},
					{
						id: 24, title: "8.2如何导出Project文件", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154508/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_24.png'
					},
					{
						id: 25, title: "8.3如何导出表格区域信息", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154509/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_25.png'
					},
					{
						id: 26, title: "8.4如何导出PDF文件", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154510/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_26.png'
					},
					{
						id: 27, title: "9.1如何导入Project文件，形成网络图", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154826/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_27.png'
					},
					{
						id: 28, title: "9.2如何使用Excel文件，形成网络图", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/154827/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_28.png'
					},
					{
						id: 29, title: "10.1AI助手- AI助手介绍+操作说明", tips: "软件学习", time: "时长：", src: 'https://jzkt.fwxgx.com/courses/24304/videos/162580/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_29.png'
					},
					{
						id: 30, title: "10.2AI助手-AI生成施工总控计划", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/162581/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_30.png'
					},
					{
						id: 31, title: "10.3AI助手-AI推荐非实体工作", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/162582/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_31.png'
					},
					{
						id: 32, title: "10.4AI助手-AI推荐工作", tips: "软件学习", time: "时长", src: 'https://jzkt.fwxgx.com/courses/24304/videos/162583/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_32.png'
					},
				],
				pics1: [
				{
						id: 1, title: "", tips: "专家课堂", time: "时长：108分钟", src: 'https://jzkt.fwxgx.com/courses/23597/videos/134798/play',
						srcimg: '/banner1/新-教学视频小节封面_01.png',
					
					},
					{
						id: 2, title: "", tips: "专家课堂", time: "时长：89分钟", src: 'https://jzkt.fwxgx.com/courses/23598/videos/134799/play',
						srcimg: '/banner1/新-教学视频小节封面_01.png'
					},
					{
						id: 3, title: "", tips: "专家课堂", time: "时长：58分钟", src: 'https://jzkt.fwxgx.com/courses/23599/videos/134800/play'
						,srcimg: '../assets/banner1/新-教学视频小节封面_03.png'
					},
				]
			}
	},
	mounted() {
    // 初次加载时显示所有内容
    this.searchResults = this.pics;
  },
  components: {

    'a-input-search': Input.Search,
  },
  props: {
    version: {
      type: String,
      required: true,
    },
    lock: {
      type: String,
      required: true,
    },
    token: {
      type: String,
      required: true,
    },
    product: {
      type: String,
      required: true,
    },
    companies: {
      type: Array,
      required: true,
    },
    isLoggedIn: {
      type: Boolean,
      required: true,
    },
    isZpertV1: {
      type: Boolean,
      required: false,
    },
    isTrialVersion: {
      type: Boolean,
      required: true,
    },
    msProject: {
      type: String,
      required: false,
      default: "",
    },
  },
  computed: {
    url() {
      let url = "";
      if (this.$route.query.type === "glodonedu") {
        url = `${this.$route.query.url}?access_token=${this.$route.query.accessToken}&channel=banma`;
      } else {
        url = `${this.$route.query.url}?invitation_code=${
          this.$route.query.invitationCode
        }&t=${Date.now()}`;
      }
      return url;
    },
  },
  methods: {
			onSearch: function(searchValue){
			  console.log('use value', searchValue);
			  console.log('or use this.value', this.value);
			},
			changeTitle(item, index) {
				this.current = index;
               if(index == 0){
                   this.searchResults = this.pics;
               }else if(index == 1){
                   this.searchResults = this.pics1;
               }
			},
	  fn(item) {
		window.location.href = item.src
			},
	  search() {
		this.searchResults = this.pics.filter(item => 
        item.title.includes(this.value)
      );
			}
  }
		
};
</script>
<style lang="less" scoped>
	.banma-warp {
		padding-top: 24px;
		padding-left: 20px;
		padding-bottom: 24px;
		padding-right: 15px;
		background-color: #F4F7FC;
                          
	}
	.condition-box {
		background-color: #f4f7fc;
		width: 100%;
		height: 56px;
		// padding: 10px 20px;
		box-sizing: border-box;
		display: flex;
		
		justify-content: start;
		// padding: 5px 5px;
		.title-box {
			display: flex;
			// border-radius: 10px;
			justify-content: start;
			// width: 68.835%;
			// flex-wrap: wrap;
			>div {
				// padding: 12px 0px ;
				box-sizing: border-box;
				width: 192px;
				margin-right: 12px;
				justify-content: space-between;
				font-size: 17px;
				display: flex;
				// align-items: center;
				// justify-content: center;
				color: white;
				border-radius: 8px;

				&:nth-child(1) {
					
					background-color: #FFE2C7;
				}
				&:nth-child(2) {
					background-color: #C3E7FC;
					
					
				}
				&:nth-child(3) {
				
					background-color: #ECDCFF;
				}
				&:nth-child(4) {
					width: 224px;
					background-color: #00D9C3;
				}
				.title-box1 {
					flex: 1;
					// background-color: red;
					margin: 6px 0 6px 16px;
					.title-boxfont1{
						font-family: HarmonyOS Sans SC;
						font-size: 18px;
						font-weight: 500;
            line-height: 24px;
						display: block;
						height: 24px;
						color: #EA8735;
					}
					.title-boxfont2 {
						display: block;
						height: 20px;
						line-height: 20x;
						font-weight: 300;
						color: #EA8735;
						font-size: 12px;
						font-family: HarmonyOS Sans SC;
					}
				}
			}
		
		}
		.active {
			border: 1px solid blue;
		}
    .search {
  display: flex;
	border-radius: 8px;
  padding: 10px 16px;
  width: 317px;
  height: 56px;
  background: #FFFFFF;
	justify-content: center;
	position: relative;
  
	input {
  //  flex: 1;
   border: 0;
   width: 285px;
	 height: 36px;
   /* 去掉表单控件的焦点框 */
   outline: none;
	 border: 1px solid #E2E8F0;
	 box-sizing: border-box;
	 padding: 7px 16px;
	 border-radius: 4px;
}
input::placeholder {
  font-family: HarmonyOS Sans SC;
font-size: 14px;
font-weight: normal;
line-height: 22px;
letter-spacing: 0em;

font-variation-settings: "opsz" auto;
/* Greyscale/500 */
/* 样式描述：单位及小字说明色 */
color: #96A0B5;
}
a {
	position: absolute;
	right: 32px;
  align-self: center;
  width: 16px;
  height: 16px;
  background-image: url(../assets/icon@1x.png);
}
}



/* ::placeholder 选中就是 placeholder 属性文字样式*/


/* 父级是flex布局，子级变弹性盒子：加宽高生效 */



	}
	// .search-box {
	// 		width: 100%;
	// 		margin-top: 20px;
			
	// 	}
	.list-box {
		width: 100%;
		display: flex;
		flex-wrap: wrap;
    margin-top: 30px;
    // padding-right: 11px;
    justify-content: start
	}
	.list-item {
		width: 214.4px;
    height: 196px;
    border-radius: 8px;
  
		background: #FFFFFF;
		padding: 0px 0px 12px 0px;
    margin-right: 24px;
    margin-bottom: 24px;
		box-sizing: border-box;
		&:nth-of-type(5n){
			margin-right: 0px;
		}
		.list-item-box {
      height: 100%;
			width: 100%;

			position: relative;
			.tips {
				padding: 4px 12px;
				color: white;
				position: absolute;
				top: 0px;
				right: 0px;
				background-color: deepskyblue;
				border-bottom-left-radius: 10px;
				border-top-right-radius: 10px;
			}
			
			img {
				width: 100%;
				border-top-left-radius: 10px;
				border-top-right-radius: 10px;

			}

			
			.list-desc {
				display: flex;
				width: 100%;
				margin-top: 13px;
				height: 22px;
        justify-content: space-between;
				
				
				.title {
					font-size: 10px;
					font-weight: 600;
					width: 70%;
					white-space: nowrap;  /* 强制不换行 */
					overflow: hidden;
					text-overflow: ellipsis;
				}
				.time {
					margin-right: 12px;
					height: 20px;
					width: 31px;
					font-family: HarmonyOS Sans SC;
					font-size: 12px;
					line-height: 20px;
					color: #64748B;
				}
			}
		}
		
	}
	
	/* 当屏幕小于1400px */
	@media screen and (min-width: 1400px){
		.list-item {
		
		&:nth-of-type(5n){
			margin-right: 24px;
		}
}
	}
	@media screen and (max-width: 1400px){
	
	}
	/* 当屏幕小于1200px */
	@media screen and (max-width: 1220px){
		.list-item {
		
		&:nth-of-type(5n){
			margin-right: 24px;
		}
}
	}
	
	/* 当屏幕小于992px */
	@media screen and (max-width: 992px){
		
		
		
	}
	/* 当屏幕小于768 */
	@media screen and (max-width: 768px){

	}
	
	
	/* 当屏幕小于700 */
	@media screen and (max-width: 700px){
	
	}
	
	
</style>