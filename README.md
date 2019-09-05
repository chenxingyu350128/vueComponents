# vueComponents 通用组件

## header头部组件

## v-slot:center应对中部复杂化的情景

## slideToDelete 滑动删除，组件内部仅提供滑动的方法（methods）,检测全体的滑动状态及滑块复位全在父组件中进行
>//判断当前是否有滑块处于滑动状态(移至父组件)
>>//复位滑动状态(移至父组件)

>>代码如下：
```
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
```
### 滑动距离distance  在组件css代码开头设置	
  :root {
		distance: 100px;
	}    
