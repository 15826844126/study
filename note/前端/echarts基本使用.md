### 安装与加载

```js
#安装
	npm i echarts -s
#加载
	(1)script载入  
    (2)项目引入
    	import * as echarts from 'echarts'
	(3)按需引入
        // 引入 echarts 核心模块，核心模块提供了 echarts 使用必须要的接口。
        import * as echarts from 'echarts/core';
        // 引入柱状图图表，图表后缀都为 Chart
        import { BarChart } from 'echarts/charts';
        // 引入提示框，标题，直角坐标系，数据集，内置数据转换器组件，组件后缀都为 Component
        import {
          TitleComponent,
          TooltipComponent,
          GridComponent,
          DatasetComponent,
          TransformComponent
        } from 'echarts/components';
        // 标签自动布局，全局过渡动画等特性
        import { LabelLayout, UniversalTransition } from 'echarts/features';
        // 引入 Canvas 渲染器，注意引入 CanvasRenderer 或者 SVGRenderer 是必须的一步
        import { CanvasRenderer } from 'echarts/renderers';

        // 注册必须的组件
        echarts.use([
          TitleComponent,
          TooltipComponent,
          GridComponent,
          DatasetComponent,
          TransformComponent,
          BarChart,
          LabelLayout,
          UniversalTransition,
          CanvasRenderer
        ]);
```

### 初始化与制作

```js
#初始化与制作
// 基于准备好的dom，初始化echarts实例
var myChart = echarts.init(document.getElementById('main'));
// 绘制图表
myChart.setOption({
  title: {
    text: 'ECharts 入门示例'
  },
  tooltip: {},
  xAxis: {
    data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
  },
  yAxis: {},
  series: [
    {
      name: '销量',
      type: 'bar',
      data: [5, 20, 36, 10, 10, 20]
    }
  ]
});
```

### 实例方法与属性

```js
	创建一个 ECharts 实例，返回 echartsInstance，不能在单个容器上初始化多个 ECharts 实例
var myChart = echarts.init(document.getElementById('main'))
#实例方法    
	(1)mychat.resize() //设置图标容器大小
	(2)mychat.setOption(options)//配置样式和属性
#属性(options)
	(1)title:{ //标题设置
    	 text：""，//标题名称
         textStyle:{//标题样式
             ....
         }
         subtext:''，//副标题
         subtextStyle:{
             ....
         },
         left:'',//标题方位
         top:''    
     
    	}
	(2)grid:{//网格布局
        
    	}
	(3)xAxis:{//x轴
          offset:{},//多个x轴设置偏移量
          type:''//x坐标轴类型 value连续数值轴 category类目轴，time连续时间轴，log对数轴	
          data:[''],//x轴数据
          name:'',//x轴名称（箭头位置）
          nameTextStyle:{//x轴名称样式
              color:'',//字体颜色
              fontStyle:'',//字体样式
              fontSize:'',//字体大小
          }，
          splitLine:{//坐标轴的分割线
              show:boolean,//是否显示分割线（田字格）
          }
          nameGap:Number,//x轴名称与x轴线距离
          inverse:Boolean，//是否反转坐标轴
          min:Number/Function,//坐标轴最小值
          max：Number/Function,//坐标轴最大值
          axisLaber:{//坐标轴刻度标签的设置
              width:'',//刻度标签的宽度
              color:"string",//刻度标签的颜色
              show:true,//是否显示刻度
              backgroundColor:'string',//刻度标签的刻度颜色
              interval:Nubmer,//显示坐标轴刻度间隔，类目轴有效，0显示所有坐标轴刻度
          	  rotate:Number,//刻度标签旋转角度（x轴上文字刻度旋转度数）
              margin:Number.//坐标刻度与轴线的上线距离
              formatter:'string'/function,//刻度标签的内容格式器
                  eg: formatter:'{value}kg' -----x轴刻度显示文字带有kg
              		  formatter:function(value,index){//参数：刻度数值，刻度索引
                          return value +'kg';
                      }
              overflow:"",//设置width宽度有效 beark换行，truncate截断（配置ellipsis文本有效默认...）
              ellipsis:'...',//配置截断内容
          }
    	}
     (4)yAxis:{}//同y轴
     (5)tooltip:{//提示框 可设置在全局或者坐标系axis，系列series中
          trigger:'',//触发类型 item数据图形触发（散点图，饼图） axis坐标轴触发（柱状图，折线图）
          triggerOn:'',//提示框触发条件 鼠标移动mousemove 鼠标点击click
          showDelay:Number,//设置提示框延迟时间
          axisPointer:{//坐标点触发显示
              type:'',//指示器类型 line直线，shadow阴影指示器，cross十字准星
          },
          showContent：'',//是否显示悬浮提示框
          fomatter:functipn(params,ticket,callback){//提示框浮层内容格式器
              
          }
     	}
     (6)polar:{//极坐标系（圆形坐标系），用于散点图
          center:['number','number'],//极坐标中心坐标，参数：[x轴]，[y轴]
          radius:['',''],//极坐标系的半径 参数:['内环','外环']
      	}
     (7)radar:{//雷达图坐标系
        	indicator:[//雷达图的指示器（雷达图上的数据）
                {
                   name:'销售'，max：Nubmer,color:'red'
                },{
                    .......
                }
            ]   
       	}  
    (8)dataZoom:[//区域缩放窗口，为位置在图下或图右方位，有三种缩放类型（内置缩放，滑动缩放，框选缩放）
             {
                 
             }
       ]
          
```

