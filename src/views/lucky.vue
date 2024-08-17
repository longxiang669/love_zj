<template>
  <div class="lucky_wheels">
    <template>
    <LuckyWheel
      ref="myLucky"
      width="90vw"
      height="90vw"
      :prizes="prizes"
      :blocks="blocks"
      :buttons="buttons"
      @start="startCallback"
      @end="endCallback"
    />
</template>
</div>
</template>

<script>
export default {
  name: 'LuckyWheel1',
  data () {
    return {
      //转盘背景
      blocks: [
        { 
          padding: '0px',     //可旋转区域与转盘边缘的距离
          background: '#eee',  //转盘背景色
          //转盘背景图
          // imgs:[
          //   {
          //     src:require('@/assets/logo.png'),   //图片url
          //     top:'0',     //图片距顶部距离
          //     width:'400px',  //图片宽
          //     height:'400px', //图片高
          //   }
          // ],
        }
      ],
      // 扇形数组
      prizes: [
        //单个扇形
        { 
          //奖品文字
          fonts: [
            { 
              text: '红色',        //文字
              top: '9%',          //文字距顶部距离
              fontColor:'#fff',    //文字颜色
              fontSize:'16px',     //文字大小
              fontStyle:'微软雅黑', //字体
              fontWeight:'500',    //加粗
              lineHeight:'16px',   //行高
              wordWrap:true,       //换行
              lineClamp:2,         //2行，剩下的...
              wordWrap:true,       //换行
            }
          ], 
          //奖品图
          // imgs:[
          //   {
          //     src:'https://img95.699pic.com/xsj/1s/5e/0g.jpg%21/fh/300',   //图片url
          //     top:'30%',     //图片距顶部距离
          //     width:'60px',  //图片宽
          //     height:'60px', //图片高
          //   }
          // ],
          background: '#dc143c',  //扇形背景色
          range:12,  //当前prize.range/所有prize中range总和
        },
        // { fonts: [{ text: '红色', top: '9%' }], background: 'red' },
        { fonts: [{ text: '粉色', top: '9%', fontColor:'#fff' }], background: 'pink' },
        { fonts: [{ text: '橙色', top: '9%', fontColor:'#fff' }], background: '#ffa500' },
        { fonts: [{ text: '绿色', top: '9%', fontColor:'#fff' }], background: '#7fffd4' },
        { fonts: [{ text: '蓝色', top: '9%', fontColor:'#fff' }], background: '#87ceeb' },
        { fonts: [{ text: '白色', top: '9%', fontColor:'#000' }], background: '#f5fffa' },
        { fonts: [{ text: '紫色磨砂', top: '9%', fontColor:'#fff' }], background: '#9370db' },
        { fonts: [{ text: '紫色润珠', top: '9%', fontColor:'#fff' }], background: '#da70d6' },
        { fonts: [{ text: '紫色透珠', top: '9%', fontColor:'#fff' }], background: '#e6e6fa' },
        { fonts: [{ text: '白色小圈', top: '9%', fontColor:'#000' }], background: '#fff5ee' },
        { fonts: [{ text: '绿色小圈', top: '9%', fontColor:'#fff' }], background: '	#7fffd4' },
        { fonts: [{ text: '彩色', top: '9%', fontColor:'#fff' }], background: '#E3556B' },
      ],
      
      buttons: [{
        radius: '35%',
        // background: '#fff',
        pointer: true,
        // fonts: [
        //   { 
        //     text: '点击抽奖',        //文字
        //     top: '-15%',          //文字距顶部距离
        //     fontColor:'#f00',    //文字颜色
        //     fontSize:'16px',     //文字大小
        //     fontStyle:'微软雅黑', //字体
        //     fontWeight:'500',    //加粗
        //     lineHeight:'16px',   //行高
        //   }
        // ],
        //抽奖按钮图
        imgs:[
            {
              src:require('@/assets/111.png'),   //图片url
              top:'-90%',     //图片距顶部距离
              width:'90%',  //图片宽
              // height:'100%', //图片高
            }
        ],
      }],
    }
  },
  methods: {
    // 点击抽奖按钮会触发star回调
    startCallback () {
      // 调用抽奖组件的play方法开始游戏
      this.$refs.myLucky.play()
      // 模拟调用接口异步抽奖
      setTimeout(() => {
		function getRandomInt(min, max) {  
		  min = Math.ceil(min); // 最小值是包含在内的，所以使用Math.ceil  
		  max = Math.floor(max); // 最大值是包含在内的，但因为Math.random()不包括max，所以这里直接使用  
		  return Math.floor(Math.random() * (max - min + 1)) + min;  
		}  
		  
		// 使用函数生成0到11之间的随机整数  
		let randomNumber = getRandomInt(0, 11);  
		console.log(randomNumber);
        // 调用stop停止旋转并传递中奖索引
        this.$refs.myLucky.stop(randomNumber)
      }, 5000)
    },
    // 抽奖结束会触发end回调
    endCallback (prize) {
      console.log(prize)
    },
  }
}
</script>
<style scoped>
.lucky_wheels {
	width: 100vw;
	height: 100vh;
	background: url('../assets/nana_0_1.png') no-repeat;
	background-size: 100% 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	padding-left: -20vw;
	box-sizing: border-box;
}
</style>

