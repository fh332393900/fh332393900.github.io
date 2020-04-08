---
title: 项目结构
date: 2020/4/8 10:46:50
categories:
- 前端
tags:
- Vue
---
## vue-element-admin项目结构



```diff
vue-element-admin
|- build
|- mock											//模拟数据
	|- article.js								//文章数据
	|- index.js
	|- mock-server.js							//mock模拟数据服务
	|- remote-search.js							//远程搜索数据
	|- user.js									//用户数据
|- public
	|- favicon.ico                 				//网站图标
	|- index.html				   				//网站首页
|- src
	|- api						   				//请求接口的地址
	|- assets 					   				//静态资源
	|- component    			   				//公用组件
    	|- BackToTop							//回到顶部
    	|- Breadcrumb							//面包屑
    	|- Charts								//图表页面组件
    	|- DndList								//拖拽组件
    	|- DragSelect							//拖拽选择器
    	|- Dropzone								//拖拽上传文件（纯手动封装）
    	|- ErrorLog								//bug日志
    	|- GithubCorner							//GitHub图标按钮
    	|- Hamburger							//菜单伸缩图标按钮
    	|- HeaderSearch							//头部搜索组件
    	|- ImageCropper							
    	|- JsonEditor							//json编辑器
    	|- Kanban								//拖拽看板组件
    	|- MarkdownEditor						//markdown编辑器
    	|- MDinput								//输入框的组件
    	|- Pagination							//分页组件
    	|- PanThumb								//圆形头像组件
    	|- RightPanel							//设置的抽屉组件
    	|- Screenfull							//全屏显示
    	|- Share								//自定义下拉菜单（纯手动）
    	|- SizeSelect							//全局字体大小选择器
    	|- Sticky								//创建文章
    	|- SvgIcon								//Svg图标
    	|- TextHoverEffect						//文本悬停特效组件
    	|- ThemePicker							//主题（色彩）选择器
    	|- Tinymce								//富文本编辑器
    	|- Upload								//上传组件
    	|- UploadExcel							//导入excel组件
    |- directive								//自定义指令
    	|- clipboard							//一键复制指令
    	|- el-drag-dialog						//弹窗可拖拽指令
    	|- el-table								//表格从页面底部开始的高度指令
    	|- permission							//权限指令
    	|- waves								//点击按钮波浪效果指令
    |- filters
    |- icons									//图标文件
    |- layout									//项目整体布局
    	|- components
    		|- Settings							//右侧设置
    		|- Sidebar							//左侧菜单栏
    		|- TagView							//标签切换
    			|- index.vue					//标签切换主要页面
    			|- ScrollPane.vue				//标签切换组件的滚动条
    		|- AppMain.vue						//主体内容区域
    		|- index.js							//导出布局的整合
    		|- NavBar.vue						//顶部区域
    	|- mixin
    	|- index.vue							//整体布局合并
    |- router									//路由
    	|- moudles								//单独提取的路由
            |- charts.js
            |- components.js
            |- nested.js
            |- table.js
    	|- index.js								//路由配置文件
    |- store									//状态管理
    |- styles									//公用的样式
    |- utils									//工具函数
    |- vendor									//导入导出excel需要引入的函数
    |- views
    	|- charts								//图表页面
    		|- keyboard.vue						//键盘图
    		|- line.vue							//折线图
    		|- mix-chart.vue					//综合图表
    	|- clipboard							//一键复制页面
    	|- components-demo						//组件demo页面
    		|- avatar-upload.vue				//上传头像页
    		|- back-to-top.vue					//回到顶部页
    		|- count-to.vue						//计算总数页
    		|- dnd-list.vue						//拖拽列表页
    		|- drag-dialog.vue					//拖拽弹窗页
    		|- drag-kanban.vue					//拖拽看板页
    		|- drag-select.vue					//拖拽选择器里选项的页面
    		|- dropzone.vue						//上传文件页面（纯手写）
    		|- json-deitor.vue					//json编辑器
    		|- markdown.vue						//markdown编辑器页面
    		|- split-pane.vue					//区域伸缩页面
    		|- sticky.vue						//吸附顶部页
    		|- tinymce.vue						//富文本编辑页
    	|- dashboard							//首页仪表盘
    	|- documentation						//文档页面
    	|- error-log							//错误日志
    	|- error-page							//401，404页面
    	|- example								//综合实例，创建文章，文章列表
    	|- excel								//导出excel，导如excel
    	|- guide								//引导页
    	|- icons								//图标icon页
    	|- login								//登录页
    	|- nested								//嵌套路由页
    	|- pdf									//pdf下载
    	|- permission							//权限页面
    	|- profile								//个人中心页
    	|- qiniu								//拖拽上传（创建文章页面）
    	|- redirect								//重定向
    	|- tab									//标签页
    	|- table								//表格页
    	|- theme								//主题选择页
    	|- zip									//导出压缩文件zip页
    |- App.vue									//项目主要页面
    |- main.js									//项目入口文件
    |- permission.js
    |- settings.js								//右侧设置的配置文件
|- tests										//测试文件
|- .env.development								//开发环境请求接口
|- .env.production								//生产环境请求接口
|- .env.staging									//测试环境请求的接口
|- vue.config.js								//vue中webpack的配置文件
```



##### webpack别名

```js
resolve: {
   alias: {
      "@": path.resolve('src')
   }
}
```

在vscode中加入jsconfig.json，智能提示路径别名

```json
{ 
    "compilerOptions": {
      "baseUrl": "./",
      "paths": {
          "@/*": ["src/*"]
      }
    },
    "exclude": ["node_modules", "dist"]
  }
```



element-ui多级嵌套的菜单，el-submenu使用递归组件时,出现了折叠后菜单标题不隐藏的问题

 出现这个问题是因为我们在 <el-menu> 嵌套中出现了意料之外的  <div>  ,而 <el-menu> 标签本身希望里面嵌套的是 <el-menu-item> ， <el-submenu> ， <el-menu-item-group> 其中之一 。

解决方法：安装vue-fragment

```shell
npm install --save vue-fragment
```



在vue入口文件按中添加

```js
import Fragment from 'vue-fragment'

Vue.use(Fragment.Plugin)
```

总结：

1.使用webpack构建项目，安装需要的依赖。

- webpack的配置分件，三个部分基础配置，开发环境配置，生产环境配置。
- npm脚本，打包项目，项目启动。

2.vue相关配置

- 项目入口，引入相应的模块与插件，样式等。
- 项目的路由，定义路由对象，最外层时layout组件，app-main为内容页面。
- vuex状态管理，来管理全局的状态，菜单栏的伸缩；标签页的打开与关闭；当前路由位置面包屑。

3.layout整体布局

- 侧边菜单栏：logo，与菜单组件，通过循环路由对象来
- navbar顶部状态栏组件：面包屑，全屏，头像组件
- 标签页组件：展示当前打开的页面，关闭页面
- app-main内容区域:页面展示的区域

4.pages页面

- 首页
- 中奖信息页面：头部是一个标题加搜索的表单，输入框与时间选择器元素；下面是一个表格的数据展示，可以在表格内编辑。
- 奖品管理页面：头部为标题，下面为表格的数据展示。
