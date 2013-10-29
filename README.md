#用yeoman, grunt 和 bower 搭建管理前端工程

##用到的工具

1. yeoman
2. grunt
3. bower

其实yeoman自身集成了grunt 和 bower，在介绍yeoman之前，先来看看grunt 和 bower 都能干些什么


###grunt： [详情请戳](http://gruntjs.com/getting-started)

GRUNT是JavaScript的构建工具，属于Node.js的一个package
可以自动化完成压缩、编译、测试等任务，也支持自己编写task。类比起来类似于rake和gradle

由于是Node.js的package， 所以安装也很简单，只要有Node.js的支持，使用npm就可以安装：

	npm install -g grunt-cli
	
典型的使用grunt的工程下应该有```package.json```和```Gruntfile```

package.json 用来列出项目中要用到的Grunt plugins.
Gruntfile 名为```Grunt.js```或者```Grunt.coffee```的文件，用来定义task和读取plugin

#####package.json

```package.json```文件应该放在项目的根目录下，并且被版本控制工具管理起来。在根目录下运行```npm install```，```package.json```中所列出的依赖就会被自动安装。

大部分的grunt-init的模板都会自动生成```package.json```文件
运行npm init也会生成基本的```package.json```文件
也可以手动添加，范例如下（具体规范[请戳](https://npmjs.org/doc/json.html)）：

	{
  		"name": "my-project-name",
  		"version": "0.1.0",
  		"devDependencies": {
    		"grunt": "~0.4.1",
    		"grunt-contrib-jshint": "~0.6.3",
    		"grunt-contrib-nodeunit": "~0.2.0",
    		"grunt-contrib-uglify": "~0.2.2"
  		}
	}
#####Gruntfile

```Gruntfile.js```或者```Gruntfile.coffee```应该是工程根目录下合法的js或者coffee script文件，和```package.json```放在一起

Grunt基本介绍。。。。。。。

###bower [详情请戳](http://bower.io/)

Bower是twitter提供给大家的web包管理工具，同样依赖于Node.js和npm。
安装也很简单：

	npm install -g bower	
	
bower需要配置```bower.json```和```.bowerc```文件
```.bowerc```文件里决定了bower的基本配置，如依赖下载后的存储地点

	{
    	"directory": "app/bower_components"
	}
	
```bower.json```里定义了如下内容

* name (required): The name of your package.
* version: A semantic version number (see semver).
* main [string|array]: The primary endpoints of your package.
* ignore [array]: An array of paths not needed in production that you want Bower to ignore when installing your package.
* dependencies [hash]: Packages your package depends upon in production.
* devDependencies [hash]: Development dependencies.
* private [boolean]: Set to true if you want to keep the package private and do not want to register the package in future.	

实例如下

	{
  		"name": "my-project",
  		"version": "1.0.0",
  		"main": "path/to/main.css",
  		"ignore": [
    		".jshintrc",
		    "**/*.txt"
		  ],
		  "dependencies": {
		    "<name>": "<version>",
		    "<name>": "<folder>",
		    "<name>": "<package>"
		  },
		  "devDependencies": {
		    "<test-framework-name>": "<version>"
  		}
	}
	
使用时只要在根目录下运行```bower install```即可根据bower.json中定义的依赖自动下载安装依赖

###Yeoman [详情请戳](http://yeoman.io/gettingstarted.html)

Yeoman能帮助我们更加规范并且快捷的创建一个前段web应用，它包含了三种核心工具 -- ```yo```，yeoman提供的脚手架工具，和前面提过的构建工具```grunt```和依赖管理工具```bower```	

#####YO

YO使用不同的generators（scanfolding templates）来生成基础web application 模板。YO和所有的
