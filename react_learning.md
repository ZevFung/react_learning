1.react.js文件是创建React元素和组件的核心文件，react-dom.js文件用来把React组件渲染为DOM，此文件依赖于react.js文件，需在其后被引入。
2.React.createClass is not a function  
这个是因为react最新版本抛弃使用了createClass这个函数，这个也是为了配合ES6 ，与时俱进 。

`<script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>`
`<script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>`
  
  


	var HelloMessage = React.createClass({
    	render: function() {
        	return <h1>Hello {this.props.name}</h1>;
        	}
		});
	ReactDOM.render(
  	    <div><h1>Hello, world!</h1><HelloMessage name="fzw"/></div>,
  		document.getElementById('root')
	);

 

3.react在unpkg包   
15版本：  
https://unpkg.com/react@15.3.2/dist/react.js  
https://unpkg.com/react-dom@15.3.2/dist/react-dom.js  
16版本：  
https://unpkg.com/react@16/umd/react.development.js  
https://unpkg.com/react-dom@16/umd/react-dom.development.js

4.
Super expression must either be null or a function, not undefined  
确认一下React.Component是否书写正确

5.React入门介绍-ReactDOM.render()等基础
首先，React是一个用于构建用户界面的Javascript库,但Peact并不是一套完整的MVC或MVVM的框架，它仅涵盖V-view视图层。JSX是javascript的扩展，像Typescript,coffeeScript等一样，都是Javascript的语法糖，最终都要变编译成JS执行，建议使用JSX的代码进行React的开发。因为Javascript代码与JSX代码并不兼容，凡是使用JSX的地方我们都需要加上 type="text/babel"。
在使用React之前，我们必须要先引入三个库——react.js/react-dom.js/browser.min.js

<html>
  <head>
    <script src="../../react.js"></script>
    <script src="../../react-dom.js"></script>
    <script src="../../browser.min.js"></script>
  </head>
  <body>
  </body>
</html>
JSX比较特殊的是允许Javascript和HTML的混写，看一个简单的例子：

   <div id="container"></div>

    <script type="text/babel">
    let value = "demo1";
    let buttonName = "submit";
      ReactDOM.render(
        <div>
          <input type="text" value={value}/> //注意单标签一定要闭合“/”,否则会报错
          <button>{buttonName}</button>//在{}中插入变量
        </div>,
        document.getElementById("container")
      )
    </script>
ReactDOM.render是React的最基本方法用于将模板转为HTML语言，并插入指定的DOM节点。ReactDOM.render(template,targetDOM),该方法接收两个参数：第一个是创建的模板，多个dom元素外层需使用一个标签进行包裹，如<div>；第二个参数是插入该模板的目标位置。若要为创建的某个元素增加class属性，不能直接定义class而要用className，因为class是javascript中的保留字。例如给input添加className并更改样式：

    <input type="text" className="userName" value={value}/> 
 
    .userName{background: yellow}//在CSS样式中定义
同样可以定义行内样式,将所有的样式包裹在一个对象中,以类似变量的形式给style属性赋值,注意样式属性要用驼峰命名法表示，如:backgroundColor而不是background-color;fongSize而不是font-size,

<input type="text" style={{"backgroundColor":"yellow","color":"red"}} value={value}/> 
另外可以直接将样式赋值给一个变量，把变量赋值给style属性，如下：

    <div id="container"></div>
    <script type="text/babel">
    let value = "demo1";
    let buttonName = "submit";
    let inputStyle = {
      "backgroundColor":"yellow",
      "color":"red"
    };
      ReactDOM.render(
        <div>
          <input type="text" style={inputStyle} value={value}/> 
          <button>{buttonName}</button>
        </div>,
        document.getElementById("container")
      )
    </script>