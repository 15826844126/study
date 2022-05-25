### 配置与安装

```js
#安装
npm install ant-design-vue --save
#按需加载
import {
  Button,
  Layout,
  Row,
  Col,
  Menu,
  Icon,
  Card,
  Tabs,
  Table,
  Form,
  Tree,
  Popover,
  Divider,
  Input,
  Select,
  Radio,
  Popconfirm,
  Message,
  Spin,
  Switch,
  Pagination,
  LocaleProvider,
  Dropdown,
  Modal,
  Upload,
  Drawer,
  DatePicker,
  InputNumber,
  Tag,
  Alert,
  Empty,
  Tooltip,
  Transfer,
  AutoComplete,
  List,
  Cascader,
  Checkbox,
  TimePicker,
  Collapse,
  Notification,
  Carousel,
  Descriptions,
  Avatar,
  Comment,
  FormModel,
  Calendar,
  Skeleton,
  Badge
} from "ant-design-vue";
Vue.use(...)
```

### 国际化

```js
ant-design-vue 目前的默认文案是英文
<template>
  <a-locale-provider :locale="locale">
    <App />
  </a-locale-provider>
</template>

<script>
  import zhCN from 'ant-design-vue/lib/locale-provider/zh_CN';
  export default {
    data() {
      return {
        locale: zhCN,
      };
    },
  };
</script>
```

### Components

```js
1.`上传` <a-upload></a-upload> 
#属性
	(1)action //上传地址
    (2)name //发送到后台文件名字
    (3)multiple //多选
	(4)directory //支持上传文件夹
    (5)showUploadList //布尔值是否展示uploadList
    (6)headers="{}" //设置上传的请求头部
	(7)listType="" //上传列表的内建样式 三种基本样式text,picture和picture-card
			text: 显示文件名  picture：显示图片+名称 
			picture-card:显示图片
#事件
	(1)change //上传中，完成，失败调用这个函数
    	@change=function(file,fileList){
        }
		file对象的内容如下：
        {
            uid:'uid',// 文件唯一标识，建议设置为负数，防止和内部产生的 id 冲突
            name: 'xx.png',   // 文件名
            status: 'done', // 状态有：uploading done error removed
            response: '{"status": "success"}', // 服务端响应内容
            linkProps: '{"download": "image"}', // 下载链接额外的 HTML 属性
            xhr: 'XMLHttpRequest{ ... }', // XMLHttpRequest Header
        }
	(2)preview //点击文件链接或预览图标时的回调 参数file
2.`栅格` <a-row>
			<a-col :sapn="24"></a-col>
	   	</a-row>

3.`间距`  <a-space ></a-space>设置组件之间的间距
#属性
	size="" //间距大小 small large 或者数字

4.`滑块`  <a-slider size=""> </a-slider>
#属性
		(1)default-value='' //默认值
        (2)setp='' //设置滑动间隔
            
            
5.`面包屑` <a-breadcrumb>
    		<a-breadcrumb-item href=""></a-breadcrumb-item>
    	</a-breadcrumb>  
#属性	
	***

6.`确认框` <a-popconfirm></a-popconfirm>

7.`按钮` <a-button> </a-button> 单个按钮
	  	<a-button-group></a-button-group> 按钮组（多个按钮连在一起）
#属性
        (1)type="" //primary主要的 dashed点线  danger危险 link链接色
        (2)disabled //禁用
        (3)ghost //反色
        (4)icon="search" //icon图标
        (5)shape="" //按钮样式 circle圆 默认矩形
        (6)loading //加载状态
        
8.`下拉菜单`<a-dropdown>
           	  <a-menu slot="overlay">
            	<a-menu-item>
            	</a-menu-item>
              </a-menu>
           </a-dropdown>   

9.`分页`<a-pagination  :total="50" show-less-items />
#属性 	
		(1)default-current="" //默认选择当前页数 
 		(2)total="" //总页数
        (3)show-size-changer //允许下拉分页
		(4)show-quick-jumper //允许选择跳转页数
		(5):current=""//当前页数
		(6)hideOnSinglePage=""//布尔值 只有一页是否隐藏分页器
		(7)pageSize=""//设置每页条数
		(8)showTotal="(total,range)=>{ }"//显示数据总量和当前数据顺序
#事件
		(1)onchange  //页码改变的回调，参数：改变后的页码，每页条数 fn(page,pageSize) 
		(2)showSizeChange //pageSize变化的回调 fn(current,size)
        
10.`自动填充`---搜索下拉填充，列表类似模糊查询
    <a-auto-complete>
        <a-select-option>
        </a-select-option>
    </a-autp-complate>
     `查询模式`
	 <a-auto-complete
         @change="search()"
            >
        <template slot="dataSource">
    		<a-select-option 
            v-for="item in dataSource" 
            :key="item.id"
            :title="item.name"
            >
                {{item.name}}
        	</a-select-option>
    	</template>
     </a-autp-complate>
 #属性	
 	(1)dataSource //填充的数据源
    (2)open //是否展开下拉菜单
    (3)defaultOpen //是否默认展开下拉菜单
    (4)disabled //是否禁用
 #事件
 	(1)change //选中 option，或 input 的 value 变化时，调用此函数
    (2)select //被选中时调用
11.`用户头像` <a-avatar/>
 #属性	size,icon,shape
		(1)src=''//用户头像路径

12.`徽标数`---消息红点或数字
		<a-badge></a-badge>
#属性
	(1) count=""//显示提示数字
	(2) number-style="{样式}"//默认提示红色
	(3) dot //消息红点
  
13.`走马灯`---实现轮播或者展图   
		<a-carousel></a-carousel>
#属性
	(1)effact="" //轮播效果fade,scrollx默认
	(2)autoplay //自动轮播
    (3)arrows //允许点击切换
    
14.`折叠面板`----点击展示列表
	  <a-collapse >
      	<a-collapse-panel key='1'></a-collapse-panel>
		#属性
        	(1)key="1"//绑定显示编号
			(2)header='' //设置列表内容
      </a-collapse>
#属性
	(1)accordion // 点击只允许单个展示
    (2)default-active-key="1" //默认展示编号列表

15.`评分rate`-----打星功能
		<a-rate />
#属性
	(1)allow-half  //允许半星
	(2):tooltips="" //弹出提示
	(3)character="" //设置评分图标 默认星号，输出A为A图标评分

16.`开关switch`
		<a-switch />
#属性
    (1)default-checked //默认打开
	(2)size='default||small' 
    (3)checked-children=""//点击提示文字
	(4)un-checked-children=""//关闭后提示文字
	(5)loading=""//加载状态
17.`空状态empty`---空白窗口暂无数据图片
		<a-empty/>

18.`文字提示tooltip`----文字汽泡框可依靠<template>或按钮渲染提示内容
    // 样式为一个带有小三角的椭圆矩形的黑色方框      
	1.<a-tooltip> -----> 用于鼠标移动触发
    	<template>
    		提示文字
    	</template>
		<div>xxxxx</div>   //触发文字
      </a-tooltip>
            
     2.<a-tooltip title="哈哈哈哈"> --->提示文字为‘哈哈哈哈’
        <button>触发文字</button> 	
       </a-tooltip>
#属性
	(1)placement="" //提示方位 top topLeft .....
	(2)title="" //提示文字
            
19.`警告提示alert`
	<a-alert>
    </a-alert>
#属性
	(1)message=""//设置提示框内容
	(2)	type=""//警告类型 error红色 warning黄色 success绿色 info蓝色
	(3):show-icon=""// 布尔值 是否显示提示小图标
	(4)closable //允许被叉掉（图标）
    (5)close-text="" //自定义关闭 设置关闭文字

20.`抽屉drwaer`----点击弹出全屏菜单框并带有遮罩层
	<a-drawer>
    	<p>1</p>
		<p>2</p>
		<p>3</p>
    </a-drawer>
#属性
	(1) title="" //抽屉标题
	(2) placement="" //弹出抽屉方位right left top bottom
	(3)	:closable="false"	//不允许叉掉
	(4):visible="" //布尔值 是否显示抽屉

21.`对话框modal`-----点击弹出确定框
	<a-modal>
    	
    </a-modal>
#属性
	(1):destroyOnClose=""// 布尔值 关闭时销毁 Modal 里的子元素
	(2):footer=""//底部内容，不需要时设置为:footer="null"
	(3):maskClosable="" //点击蒙层是否允许关闭 默认true
	(4)v-model="visible" //对话框是否可见 visible为布尔值

22.`加载框spin`
	<a-spin />
#属性
	(1):spinning="" //布尔值 加载状态
	(2):delay="" //延迟出现加载时间

23.`回到顶部` ---点击图标到浏览器顶部
	<a-back-top>
    	//这里设置样式标签
    </a-back-top>

24.`分割线divder` ---默认水平分割
	<a-divder />或 <a-divder></a-divder>
#属性
	(1)type=""//分割线类型 水平horizontal或竖直vertical
    (2)dashed //默认false 虚线
    (3)orientation="" //设置虚线提示文字位置 left right

25.`小标签tag`----用于标记的小标签
	<a-tag></a-tag>
#属性
	(1)closable="" //是否可以被叉掉
	(2)color=""//设置颜色
	
26.`导航菜单`
  <a-menu>
    <a-menu-item>菜单项</a-menu-item>
	#属性
    (1)disabled=''//布尔值 是否被禁用
	(2)key=''//绑定这个菜单项的标识
	(3)title=""//设置收缩展示的悬浮标题
    <a-sub-menu title="子菜单">
      <a-menu-item>子菜单项</a-menu-item>
    </a-sub-menu>
  </a-menu>
#属性
	(1)mode=""//菜单类型 垂直vertical 水平horizontal 内嵌inline

27.`select选择器`----下拉选择
	<a-select>
   		<a-select-option></a-select-option>
		#属性
			(1)disabled //是否禁用
            (2)loading //加载状态
    </a-select>
#属性
	(1)defalut-value=""//默认选中的值
	(2)disabled //是否禁用
    (3)mode=''//设置select的模式为多选或标签 multiple多选 tags标签
	(4)allowClear //支持清除
    (5)showSearch // 布尔值使单选模式可搜索
    (6)defaultOpen //布尔值 是否默认展开下拉菜单
    (7)dropdownMatchSelectWidth //布尔值 下拉菜单和选择器同宽
    (8)notFOundContent="" //下拉列表为空时显示的内容 默认Not Found
	(9)showArrow //是否显示下拉小箭头
    (10):filterOption="function(inputValue)"//是否根据输入项进行筛选
    (11)mode='default' | 'multiple' | 'tags' | 'combobox'//设置 Select 的模式为多选或标签
    (12)open='' //是否展开下拉菜单
#事件
	(1)dropdownVisibleChange //展开下拉菜单的回调
    (2)search //文本框值变化时回调
    (3)change //选中 option，或 input 的 value 变化（combobox 模式下）时，调用此函数
    (4)select //被选中时调用，参数为选中项的 value (或 key) 值
eg:
   <a-select
        style="width: 300px"
        allowClear
        showSearch
        placeholder="请输入船舶名称"
        option-filter-prop="children"
	    :filter-option="filterOption"
        @search="searchShip"
          v-decorator="[
                'id',
                {
                  rules: [
                    {
                      message: '请输入船名',
                    },
                  ],
                },
              ]"
            >
          <a-select-option v-for="item in shipNameArr" :key="item.id" :value="item.id">
                {{item.name }}
           </a-select-option>
   </a-select>
#在methods中：
	filterOption(input, option) {//模糊查询
               return
        	(option.componentOptions.children[0].text.toLowerCase().indexOf(input.toLowerCase()) >= 0
      );
    },
        
        
28.`穿梭框transfer` ---双栏穿梭选择框   
	<a-transfer
        :dataSource="mockData"
        :titles="['左','右']"
     >
    
    </a-transfer>
#属性 
	(1):titles="['左','右']" //穿梭框的两边标题
    (2)dataSource //数据集
    	dataSource=[
                {
                    key: string.isRequired,
                    title: string.isRequired,
                    description: string,
                    disabled: bool
                }
            ]
    (3):operations="[]"//操作文案集合 穿梭框之间的左右选择箭头 默认值为['>', '<']
    (4)showSearch //是否显示搜索框 默认为false
    (5)showSelectAll //是否展示全选勾选框  默认值为true 
    (6):targetKeys="[]" //显示在右侧框数据的 key 集合
   	(7):listStyle="{}"//两个穿梭框的自定义样式

29.`树形控件tree` ---点击子级分类菜单 *****
    <a-tree
	 :tree-data="treeData" //树形结构数据
	 showIcon //是否显示树形图标,没有默认图标需要自行配置
     selectedKeys //array 被选中的树节点
	>	    
       <a-icon slot="search" type="search"> //设置自定义菜单图标 配合showIcon属性使用
    </a-tree>
	#属性 
    (1)autoExpandParent //布尔值 是否自动展示父节点
    (2)treeData //存放的树形结构数据
    	eg：const treeData=[
            {
                title:'string'，
                key:'string',
                children:[
                	title:'string',
                	key:'string',
                	disabled:Boolean,//禁用 可选
                	selectable：Boolean，//被选择 可选
                	......
                ]
            }
        ]
   (3)showLine //是否展示连接线   
   (4)selectedKeys //设置选中的树节点
   (5)showIcon //设置是否显示树形图标
   (6)selectable //设置 是否被选中
   (7)defaultExpandAll //false 默认展开所有树节点
   (8)defaultExpandParent //true 默认展开父节点
   (9)draggable //false 设置节点可拖拽
   #事件
   (1)select="onSelect" //点击节点触发 参数：（被选中的子节点，事件本身）
   	eg:onSelect(selectedKeys,e){
        if(e.selected){//防止被取消选中
            
        }
    }
  (2)expand// 展开/收起节点时触发
  
30.`日期控件datePicker` ---时间输入选择框 
<a-date-picker
   defaultValue=""//默认日期
   format="" //设置日期格式 YYYY-MM-DD HH:SS
   showTime //添加时间选择功能
   v-modal="value" //日期
	
>
</a-date-picker>    
```

### 表单

```js
具有数据收集、校验和提交功能的表单
`表单` <a-form>
    		<a-form-item> //单个表单框使用
			#属性
            	(1)laber="" //表单名称显示
				<----1输入框----->
				<a-input></a-input>
				#属性
                	(1)placeholder="提示信息"
					(2)prefix="" //设置输入框内左边文字
					(3)suffix=""//设置输入框内右边文字
				<----2下拉选择框---->
                 <a-select>
                     <a-select-option>
                        xxxx
                     </a-select-option>
                 </a-select>
				
				<----3表单域---->
                  <a-textarea />
                    #属性
                		(1) auto-size 自适应
                        
                <----4输入搜索框---->
                  <a-input-search />  
                    #属性
                		(1)enter-button //设置搜索图标 可设文字
						(2)loading  //设置加载状态
                
                <----5数字输入框---->
                  <a-input-number />
                  	#属性
                		(1):min=""//设置最小数字
						(2):max=""//设置最大数字
						(3):default-value=""//设置默认值
						(4):setp=""//设置调幅精度 默认为1
			</a-form-item>
      </a-form>

#属性
	(1):form="form"//第二个form在data中关联  经 Form.create() 包装过的组件会自带 this.form 属性，如果使用 template 语法，可以使用 this.$form.createForm(this, options)		在data()中设置form: this.$form.createForm(this),设置以后就可以在组件使用this.form上的方法
	(2)layout="" //布局 'horizontal'|'vertical'|'inline'
	(3):label-col="{ span: 8 }"  //label布局 设置span和offset
	(4):wrapper-col="{ span: 14 }" //需要为输入控件设置布局样式时,同label-col
	
```

#### 表单校验

```js
v-decorator=[
    'name',
    {
        rules:[//设置校验规则
			{	
                initialValue: "",//初始化值，也就是默认值,可不写
                required:true,//必须
                message:'xxxxxx',//未输入提示信息，
                pattern:/^     &/,  //正则规则，可选
            }，
            {
             validator:funtion(rule,value,callback){//自定义校验（callback必须被调用）							 if (!value) {
                        callback()
                      } else {
                        callback('您输入的验证码不正确!')
                      }
    				}
        		
    			}
            }
        ]
    }
]

# this.form方法
(1)this.formvalidateFields()  校验并获取一组输入域的值与 Error
	eg：this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
(2)this.form.setFieldsValue()   设置一组输入控件的值
	eg:this.form.setFieldsValue({
         name: `Hi, ${value === 'male' ? 'man' : 'lady'}!`,//这个name可以任意设置名称，与v-decorator中name相同
    })
(3)this.form.resetFields() 重置一组输入控件的值（为 initialValue）与状态，如不传入参数，则重置所有组件 
(4)this.form.getFieldDecorator(id, options)用于和表单进行双向绑定，单文件 template 可以使用指令v-decorator进行绑定  
	
```

### 表格

```js
对数据进行排序、搜索、分页、自定义操作等复杂行为
表格的数据源 dataSource 为一个数组 
<a-table>
#属性
	(1):rowKey="record => record.id" //表格每一行都必须有一个key值
	(2):columns="columns" //表格列的配置描述，绑定columns，自定义后还需要在data()中注册
	(3):pagination="false"//布尔值，表格的分页，推荐使用分页组件
	(4):dataSource="dataSource" //列表数据 需要在data()注册
	(5) bordered //布尔值默认false 是否展示外边框 
	(6):rowSelection="{ //列表项是否被选择
		#rowSelection配置项
        selecedRowkeys:[]//指定选中项的key数组，需要和 onChange 进行配合
		onChange:function(selectedRowKeys, selectedRows) //选中项发生变化的回调
}" //选中功能
	(7)customRow="function(record,index)"//设置行属性
		eg:props: {
            xxx... //属性
          },
          on: { // 事件
            click: (event) => {},       // 点击行
            dblclick: (event) => {},
            contextmenu: (event) => {},
            mouseenter: (event) => {},  // 鼠标移入行
            mouseleave: (event) => {}
          }

eg:
<a-table :columns="columns" :data-source="data">
    <a slot="name" slot-scope="text">{{ text }}</a>
  </a-table>
</template>
//插槽绑定的数据对象
const columns = [
  {
    title: 'Name', //表格头一列标题文字
    dataIndex: 'name',
    key: 'name',
    scopedSlots: { customRender: 'name' },//用来支持表格中的slot-scope属性
  },
  {
    title: 'Age',
    dataIndex: 'age',
    key: 'age',
    width: 80,
  },
]
//表格里的数据
const dataSource = [
  {
    key: '1',
    name: 'John Brown',
    age: 32,
    address: 'New York No. 1 Lake Park, New York No. 1 Lake Park',
    tags: ['nice', 'developer'],
  },
  {
    key: '2',
    name: 'Jim Green',
    age: 42,
    address: 'London No. 2 Lake Park, London No. 2 Lake Park',
    tags: ['loser'],
  },
  {
    key: '3',
    name: 'Joe Black',
    age: 32,
    address: 'Sidney No. 1 Lake Park, Sidney No. 1 Lake Park',
    tags: ['cool', 'teacher'],
  },
];

export default {
  data() {
    return {
      dataSource,//表格具体数据
      columns,//列描述属性数据
    };
  },
};
```

#### 插槽渲染

```js
<span slot="name" slot-scope='text,record'></span>
在scirpt中定义columns
const columns=[
    .......
	{
        title:'',//表格列表标题
    	align:''，//样式
    	width:''，//
    	ellipsis: true ,//开启标题内容溢出省略
    	scopedSlots:{custonRender:'name'}//这个name与标签中的slot关联 支持配置slot-scope
    }    
]

#columns配置项
	(1)dataIndex：string//列数据在数据项中对应的 key
    (2)customRender:Function(text, record, index) {}|slot-scope//生成复杂数据的渲染函数，参数分别为当前行的值，当前行数据，行索引
	(3)scopedSlots:{ customRender:'xxx'} // 使用 columns 时，可以通过该属性配置支持 slot-scope 的属性
	(4)align:''//设置列内容的对齐方式
	(5)ellipsis//布尔值
	(6)width:''//列宽度
	
```

### 选项卡/标签页

```js
<a-tabs>
	<a-tab-pane key="1" tab="标题1">
    	内容1
    </a-tab-pane>
	<a-tab-pane key="2" tab="标题2">
    	内容2
    </a-tab-pane>
	<a-tab-pane key="3" tab="标题3">
    	内容3
    </a-tab-pane>
	#属性
    	(1)tab="" //标题文字  必选
		(2)key=""//绑定key 必选
		(3)forceRender //被隐藏时是否渲染DOM结构 布尔值 默认false
</a-tabs/>
#属性
	(1)defaule-active-key=""//默认选择哪一项  为key属性的数值
	(2)tabPosition="left|right|top|bottom" //选项卡的方位 默认是top
	(3)closeable=""//布尔值 选项卡选项是否可以被叉掉，需要设置type为editable-card使用
	(4)type="line|card|editable-card" //选项卡的基本样式 默认line样式 card样式为方框选项，editable-card样式使用后可以允许叉掉选项卡选项与closeable配合使用
	(5)activeKey //当前激活选项的key (v-model)
#事件
	(1)change //切换面板的回调 function(activeKey){} ---参数为activeKey 激活的选项
    (2)edit  //新增和删除页签的回调 ，在type='editable-card'有效
```

### Message全局提示

```js
 this.$message方法（成功、失败、警告）
(1)this.$message.info('成功提示内容',延迟关闭弹窗提示时间) //默认提示时间为3秒，
(2)this.$message.error('失败提示内容')
(3)this.$message.warning('警告提示内容')
(4)this.$message.loading('等待提示内容')
	#eg:
	 this.$message.loading({ content: 'Loading...', key });
      setTimeout(() => {
        this.$message.success({ content: 'Loaded!', key, duration: 2 });
      }, 1000);

```


