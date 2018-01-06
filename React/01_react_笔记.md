##1. 几个重要概念理解
  * 模块与组件
    * 模块:
      * 理解: 向外提供特定(局部)功能的js程序, 一般就是一个js文件
      * 为什么: js代码更多更复杂
      * 作用: 复用js, 简化js的编写, 提高js运行效率
    * 组件: 
      * 理解: 用来实现特定功能效果的代码集合(html/css/js)
      * 为什么: 一个界面的功能更复杂
      * 作用: 复用编码, 简化项目编码, 提高运行效率
  * 模块化与组件化
    * 模块化:
      * 当应用的js都以模块来编写的, 这个应用就是一个模块化的应用
    * 组件化:
      * 当应用是以多组件的方式实现功能, 这上应用就是一个组件化的应用
##2. React的基本认识
###1）.	ReactJS是什么?
  * Facebook开源的一个js库
  * 一个用来动态构建用户界面的js库
  * React的特点
    * Declarative(声明式编码)
    * Component-Based(组件化编码)
    * Learn Once, Write Anywhere(支持客户端与服务器渲染)
    * 高效
    * 单向数据流
###2）.  React高效的原因
  * 虚拟(virtual)DOM, 不总是直接操作DOM(批量更新, 减少更新的次数) 
  * 高效的DOM Diff算法, 最小化页面重绘(减小页面更新的区域)
	####		
		在React中，构建UI界面的思路是由当前状态决定界面。前后两个状态就对应两套界面，
		然后由React来比较两个界面的区别`
##3. 使用React
###1. 相关js库
* 
		  react.js: React的核心库
		  react-dom.js: 提供操作DOM的扩展库
		  babel.min.js: 解析JSX语法代码转为纯JS语法代码的库
  * 导入相关js库文件(react.js, react-dom.js, babel.min.js)
	###
		  <script type="text/javascrisrc2 src="../js/react.js"></script>
		  <script type="text/javascrisrc2 src="../js/react-dom.js"></script>
		  <script type="text/javascrisrc2 src="../js/babel.min.js"></script>
  * 编码:	
	####
		  <div id="container"></div>
		  <script type="text/babel">
		  	var aa = 123
		    ReactDOM.render(<h1>{aa}</h1>, containerDOM);
		  </script>
##4. JSX
* 全称: JavaScript XML
  * react定义的一种类似于XML的JS扩展语法: XML+JS
  * 作用: 用来创建react虚拟DOM(元素)对象
	* 注意1: 它不是字符串, 也不是HTML/XML标签
	* 注意2: 它最终产生的就是一个**JS对象**
	* 基本语法规则
      * 遇到 <开头的代码, 以标签的语法解析: html同名标签转换为html同名元素, 其它标签需要特别解析
      * 遇到以 { 开头的代码，以JS的语法解析: 标签中的**js代码必须用{}包含**
	* 在解析显示js数组时, 会自动遍历显示-
	* 把数据的数组转换为标签的数组:
	###
		var liArr = dataArr.map(function(item, index){
			return <li key={index}>{item}</li>
		})
	* 注意:
    * 标签必须有结束
    * 标签的class属性必须改为className属性
    * 标签的style属性值必须为: {{color:'red', width:12}}
##5. 渲染虚拟DOM(元素)
	1). 语法: ReactDOM.render(virtualDOM, containerDOM) :
	2). 作用: 将虚拟DOM元素渲染到真实容器DOM中显示
	3). 参数说明
    	* 参数一: 纯js或jsx创建的虚拟dom对象
    	* 参数二: 用来包含虚拟DOM元素的真实dom元素对象(一般是一个div)
##7. Component : React是面向组件编程的(组件化编码开发)
* 基本理解和使用
	###
	* 自定义的标签: 组件类(函数)/标签
	* 创建组件类
		###
				//方式1: 无状态函数(最简洁, 推荐使用)
				function MyComponent1() {
					return <h1>自定义组件标题11111</h1>;
				}
				//方式2: ES6类语法(复杂组件, 推荐使用)
				class MyComponent3 extends React.Component {
					render () {
				  		return <h1>自定义组件标题33333</h1>;
					}
				}
				//方式3: ES5老语法(不推荐使用了)
				var MyComponent2 = React.createClass({
					render () {
				  		return <h1>自定义组件标题22222</h1>;
					}
				});
	* 渲染组件标签
		###
				ReactDOM.render(<MyComp />,  cotainerEle);
	* 注意: 
		* 返回的组件类必须首字母大写
		* 虚拟DOM元素必须有且只有一个**根元素**
		* 虚拟DOM元素必须有结束标签
	* ReactDOM.render()渲染组件标签的基本流程
	  * React内部会创建组件实例对象/调用组件函数, 得到虚拟DOM对象
	  * **组件必须**以< />便签结束符的形式来传递
	  * 将虚拟DOM并解析为真实DOM
	  * 插入到指定的页面元素内部
	* <font color="#c7254e">`props`</font>
		* 每个组件对象都会有<font color="#c7254e">`props`</font>(properties的简写)属性
		* **组件标签**的所有属性都保存在<font color="#c7254e">`props`</font>中
		* 给标签指定属性, 保存外部数据(可能是一个function)
		* **ES6类语法** 组件内部读取某个属性值:<font color="#c7254e">`this.props.propertyName`</font>
			####
				class Welcome extends React.Component {
					render() {
						return <h1>Hello, {this.props.name}</h1>;
				  	}
				}
		* **工厂模式** 组件内部读取某个属性值：<font color="#c7254e">`props.propertyName`</font>
			####
				function Welcome(props) {
					return <h1>Hello, {props.name}</h1>;
				}
		* 作用: 通过标签属性从组件外向组件内传递数据(只读)
		* 对<font color="#c7254e">`props`</font>中的属性值进行类型限制和必要性限制
			###
			    Person.propTypes = {
				    name: React.PropTypes.string.isRequired,
				    age: React.PropTypes.number.isRequired
			    }
					//name值必须有且为string,
					//age值必须有且为number
    * 扩展属性: 将对象的所有属性通过<font color="#c7254e">`props`</font>传递
   		* 	
				<Person {...person1}/> 
					遍历person1 中的属性名，
				<Person name={person2.name} 
					将person2.name的值 赋值给name属性，再传入组件内部
	* 组件的组合
		* 组件标签中包含子组件标签
		* 拆分组件: 拆分界面, 抽取组件
		* 通过<font color="#c7254e">`props`</font>传递数据
		* 组件内部想要使用外部的数据，必须在渲染时以组件标签的形式传入属性，内部通过<font color="#c7254e">`this.props`</font>的方法调用
		* 内部组件在render return 时等同于渲染。
	* <font color="#c7254e">`refs`</font>
		* 组件内包含ref属性的标签元素的集合对象
		* 给操作目标标签指定ref属性, 打一个标识
		* 在组件内部获得标签对象: this.refs.refName(只是得到了标签元素对象)
		* <font color="#c7254e">`event.target`</font> 事件属性可返回事件的目标节点（触发该事件的节点）
		* 作用: 操作组件内部的真实标签dom元素对象
	* 事件处理
		* 给标签添加属性事件名用小驼峰命名法: onXxx={this.eventHandler}
		* 在组件中添加事件处理方法**（自定义方法）**
		###
			    eventHandler(event) {
			        evnet.target可以替代this 
			    }
		###
	* React.js this 指向
		* 组件内置的方法中的this为组件对象
    	* 在组件中自定义的方法中的this为null
	    * 强制绑定this
			* 1）箭头函数(ES6模块化编码时才能使用)。
			* 2）在constructor()中bind(this)
	  			* 构造函数中的this指向实例对象 所以在constructor中的this为实例对象。
	  			* this.handleClick = this.handleClick.bind(this)。
	  			* handleClick定义在实例对象的原型上，等号右边第一个this为实例对象。所以this.handle可以找到方法。
	  			* bind（this）是指向实例对象。
	  	###	  
	* state
		* 组件被称为"状态机", 页面的显示是根据组件的state属性的数据来显示
		* 初始化指定:
		###
		        constructor() {
		          super();
		          this.state = {
		            stateName1 : stateValue1,
		            stateName2 : stateValue2
		          };
		        }

	* 读取显示: 
	    ###
			this.state.stateName1
	* 更新状态-->更新界面 : 
	    ###
			this.setState({stateName1 : newValue})
			注意：更新状态时，传入参数必须和state定义参数同名
			setState()内有个{}
	* 实现一个双向绑定的组件
		* React是单向数据流
		* 需要通过onChange监听手动实现
	* 组件生命周期
		* 组件的三个生命周期状态:
		* Mount：插入真实 DOM
		* Update：被重新渲染
		* Unmount：被移出真实 DOM
    * 生命周期流程:
      * 第一次初始化显示
		###
		      constructor()
		      componentWillMount() : 将要插入回调
		      render() : 用于插入虚拟DOM回调
		      componentDidMount() : 已经插入回调
      * 每次更新state
		###
	          componentWillReceiveProps(): 接收父组件新的属性
	          componentWillUpdate() : 将要更新回调
	          render() : 更新(重新渲染)
	          componentDidUpdate() : 已经更新回调
      * 删除组件
	    ###
	          ReactDOM.unmountComponentAtNode(document.getElementById('example')) : 移除组件
	          componentWillUnmount() : 组件将要被移除回调
    * 常用的方法
    	###
		      render(): 必须重写, 返回一个自定义的虚拟DOM
		      constructor(): 初始化状态, 绑定this(可以箭头函数代替)
		      componentDidMount() : 只执行一次, 已经在dom树中, 适合启动/设置一些监听
##8. ajax
* React没有ajax模块
* 集成其它的js库(如axios/fetch/jQuery/), 发送ajax请求
	* axios
	    * 封装XmlHttpRequest对象的ajax
	    * promise
	    * 可以用在浏览器端和服务器
	    * 下载 <font color="#c7254e">`axios`</font> 包
	    ###  
			 npm install axios --save
	    
		* 获取数据
		###
			 axios.get(url)
				 .then(response=>{
					 let data = response.data;
					 //向url发送请求，返回的数据放在response.data中
				 })
	* fetch
	    * 不再使用XmlHttpRequest对象提交ajax请求
	    * fetch就是用来提交ajax请求的函数, 只是新的浏览才内置了fetch
	    * 为了兼容低版本的浏览器, 可以引入fetch.js
	* 在哪个方法去发送ajax请求
	  * 只显示一次(请求一次): componentDidMount()
	  * 显示多次(请求多次): componentWillReceiveProps()
	
##Web Storage详解
* HTML5为我们带来了全新的本地存储方式：
	* <font color="#c7254e">`localStorage`</font>
		* localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
	* <font color="#c7254e">`sessionStorage`</font>
		* sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此<font color="#c7254e">`sessionStorage`</font>不是一种持久化的本地存储，仅仅是会话级别的存储。
			###
* web Storage 与 <font color="#c7254e">`Cookie`</font> 的区别
	* Web Storage的概念和Cookie相似，区别是它是为了更大容量存储设计的。Cookie的大小是受限的，并且每次你请求一个新的页面的时候Cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。
	* 除此之外，Web Storage拥有setItem,getItem,removeItem,clear等方法，不像cookie需要前端开发者自己封装setCookie，getCookie。		
	* 但是Cookie也是不可以或缺的：Cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在 ，而Web Storage仅仅是为了在本地“存储”数据而生（来自@otakustay 的纠正）		
		###
* localStorage和sessionStorage操作
	* setItem存储value
		
			用途：将value存储到key字段
			用法：	.setItem( key, value)
			代码示例：	
					sessionStorage.setItem("key", "value");
					localStorage.setItem("key", "value");

	* getItem获取value

			用途：获取指定key本地存储的值
			用法：	.getItem(key)
			代码示例：
					var value = sessionStorage.getItem("key"); 
					var value = localStorage.getItem("key");
	* removeItem删除key

			用途：删除指定key本地存储的值
			用法：	.removeItem(key)
			代码示例：
					sessionStorage.removeItem("key"); 	
					localStorage.removeItem("key");
  	* clear清除所有的key/value

			用途：清除所有的key/value
			用法：	.clear()
			代码示例：
					sessionStorage.clear(); 
					localStorage.clear();
## 虚拟DOM
  * 虚拟DOM是什么?
    * 一个虚拟DOM(元素)是一个一般的js对象, 准确的说是一个对象树(倒立的)
    * 虚拟DOM保存了真实DOM的层次关系和一些基本属性，与真实DOM一一对应
    * 如果只是更新虚拟DOM, 页面是不会重绘的
  * Virtual DOM 算法的基本步骤
    * 用 JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中
    * 当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异
    * 把2所记录的差异应用到步骤1所构建的真正的DOM树上，视图就更新了
  * 进一步理解
    * Virtual DOM 本质上就是在 JS 和 DOM 之间做了一个缓存。
    * 可以类比 CPU 和硬盘，既然硬盘这么慢，我们就在它们之间加个缓存：既然 DOM 这么慢，我们就在它们 JS 和 DOM 之间加个缓存。CPU（JS）只操作内存（Virtual DOM），最后的时候再把变更写入硬盘（DOM）。