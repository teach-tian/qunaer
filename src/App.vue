<template>
  <div id="app">
<!--	  exclude后边跟组件的名字意思就是所除了Detail组件不会被缓存其他都会被缓存-->
<!--	  exclude="Detail"-->
   <transition :name="trasitionName">

	  <keep-alive exclude="Detail">
		  <router-view class="Router"/>
	  </keep-alive>

	    


   </transition>  
  </div>
</template>


<script>

export default {
   name:'App',
   data(){
	   return {
		   trasitionName:'left-slide'
	   }
   },
   watch:{
	   $route(to,from){
		//   console.log(to);
        if(to.name=='Detail'){
			this.trasitionName='slide-left'
		}else if(to.name=='home'){
			this.trasitionName='slide-right'
		}
		  
	   }
   }
}

</script>

<style>

.Router{
	/* transition: all .8s ease; */
	position: absolute;
	left:0;
	top:0;
	width: 100%;
}

.slide-left-leave{
	opacity: 1;
}
.slide-left-leave-to{

	transform: translateX(-100%);
}
.slide-left-enter{

	transform: translateX(100%);
}
.slide-left-enter-to{

}


.slide-right-leave{

}
.slide-right-leave-to{

	transform: translateX(100%);
}
.slide-right-enter{

	transform: translateX(-100%);
}
.slide-left-enter-to{

}
.slide-left-leave-active,.slide-left-enter-active,.slide-right-enter-active,.slide-right-leave-active{
	transition: all 0.8s ease;
}
</style>
