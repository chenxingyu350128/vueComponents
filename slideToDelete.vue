<!-- 滑动删除组件 -->
<template>
	<div class="slideToDelete-cpnt white">
		  <v-flex 
				class="list-item grey--text text--darken-2" 
				xs12  
				data-type="0">
				<div 
					@touchstart.capture="touchStart" 
					@touchend.capture="touchEnd" 
					>
					<slot class="d-flex align-center justify-space-between pa-2" name="main">
					</slot>
				</div>
				<div class="delete height-fill">
					<slot name="delete"></slot>
				</div>
		  </v-flex>		
	</div>
</template>

<script>
	export default {
		data: ()=>({
			startX: 0,
			endX: 0,
		}),
		methods: {
			//滑动开始
      touchStart(e){
        // 记录初始位置
        this.startX = e.touches[0].clientX;
      },
      //滑动结束
      touchEnd(e){
        let a=e.currentTarget
        // 当前滑动的父级元素
        let parentElement = e.currentTarget.parentElement;
        // 记录结束位置
        this.endX = e.changedTouches[0].clientX;
        // 左滑
        if( parentElement.dataset.type == 0 && this.startX - this.endX > 30 ){
            parentElement.dataset.type = 1;
        }
        // 右滑
        if( parentElement.dataset.type == 1 && this.startX - this.endX < -30 ){
            parentElement.dataset.type = 0;
        }
        this.startX = 0;
        this.endX = 0;
      },
			//判断当前是否有滑块处于滑动状态(移至父组件)
      //复位滑动状态(移至父组件)
			/*
			代码如下：
			checkSlide(){
        const listItems = document.querySelectorAll('.list-item');
				let isSlide = false
				listItems.forEach(res=>{
					if(res.dataset.type==1){
						isSlide = true
					}
				})
				return isSlide
      },
      resetSlide(){
        const listItems = document.querySelectorAll('.list-item');
        // 复位
				listItems.forEach(res=>{
					res.dataset.type = 0
				})
      },				
			*/
			
		}
	}
</script>

<style lang="scss">
	// 滑动距离
	:root {
		distance: 100px;
	}
	.slideToDelete-cpnt{
		.list-item{
			position: relative;
			-webkit-transition: all .2s;
			transition: all .2s;
			.delete{
				width: var(distance);
				height:100%;
				background: #e01212;
				color: #fff;
				text-align: center;
				position: absolute;
				top:0;
				right: -var(distance);
			}
		}		
		.list-item[data-type="0"]{
				transform: translate3d(0,0,0);
		}
		.list-item[data-type="1"]{
				transform: translate3d(-var(distance),0,0);
		}		
	}
</style>
