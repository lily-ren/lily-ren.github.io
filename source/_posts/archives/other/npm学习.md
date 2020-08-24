---
title: npm学习总结
tag: 杂项
---
### npm学习总结

#### -一些指令：

##### 	-初始化:

​		-npm init  npm init -y (自动生成package.json)---npm i。npm i express 可以一次安装多个包。

​		-npm i -g pkg：在全局安装包。

​		-npm i -S(--save) pkg：安装包作为依赖。--dep

​		-npm i -D(--save-dev pkg):安装包作为开发依赖。--devD

​		-npm config set ---初始化默认配置。还可以配置其他的源来安装js包。使用不同团队的东西之前要注意切换set的地址。`npm set registry http://registry-npm.firstshare.cn`

​			-npm config ls -l---查看npm内部的默认配置参数。

​		-npm preinstall--客户无感知安装。 项目的 `package.json` 里增加 `preinstall` 要执行的脚本，这样合作方可以无感知的安装。

​		-npm ci---全新的安装包，对package-lock.json友好。

##### 	-运行测试：

​		-npm test（t）---

##### 	-查看项目中可用脚本：

​		-cat package.json

##### 	-npm scripts：

​		-作用：预定义前后钩子，自定义脚本。

​		-npm run env：列出项目中所有的npm环境变量

##### 	-删除重复的包：

​		-npm dedupe(ddp)---删除重复的依赖项。

##### 	-扫描应用程序中的漏洞：

​		-npm audit ---扫描项目中的任何依赖中的任何漏洞。npm audit fix 会自动安装所有漏洞包的补丁版本。

##### 	-本地测试你的软件包：

​		-npm link (模块名)：实现任意位置的npm模块命令的全局可执行。（不加模块名则是开发一个全局的模块。）

##### 	-列出所有已安装的软件包：

​		-npm list（ls）---加depth=1可以限制搜索深度。

##### 	-拓展nrm:

​			-nrm ls---查看已有的npm

​			-nrm add 源名称 url---添加相关源

​			-nrm del 源名称---删除相关源

​			-nrm use 源名称---切换相关源

​			-nrm test ---测试源速度

#### -工程上使用到npm的地方：

​	-node_modules目录：每个包都会将该包的依赖安装到当前包所在的`node_modules`目录中。（包要使用的依赖都会安装在里面。）从npm5.x增加了package-lock.json

​	-package-lock.json的详细描述主要由version、resolved、integrity、dev、requires、dependencies这几个字段构成：

​		-version---版本

​		-resolved---安装源

​		-interity---表明包完整性的hash值（验证包是否失效）

​		-dev---如果为true，则此依赖关系仅是顶级模块的开发依赖关系或者是一个的传递依赖关系

​		-requires---依赖包所需要的所有依赖项，对应依赖包`package.json`里`dependencies`中的依赖项。

​		-dependencies---依赖包`node_modules`中依赖的包，与顶层的`dependencies`一样的结构

#### 拓展---package.json中的配置：

​	-scripts：存放一些npm run xx相关的指令。会告诉你指令相关运行时什么。也可以自定义脚本命令。（npm run有串行&&和并行&两种）执行相应命令时都会执行Pro/post钩子函数。钩子函数中定义了命令执行前后的命令。

​	-dependencies：基本依赖，写在一个简单的对象中，将依赖程序包映射到版本范围。(就是项目在线上运行时所要使用到的依赖。）

​	-devDependencies：是开发时所要使用到的依赖，在线上时并不需要他们。

​		-包含什么：构建工具（webpack相关:为了生成生成环境代码。线上使用的代码是他们的工作结果）预处理器（css的相关预编译器，js中的ts，coffee-script，babel等）测试工具（chai，e2e等）其他（webpack-dev-server 支持开发热加载，线上是不用的。等这样的东西。）

​	-peerDependencies、bundleDependencies、optionalDependencies：作为npm包的发布者需要考虑使用的。后面再讲。

​	-注意版本号前的^和~：前者被优先考虑，是会把当前库中的最新版本更新到当前使用的最新版本。比如3.3.4，库会匹配3.x中的最新版本。（作用于版本号的第一个值）后者则是作用域版本号的中间的号。比如3.3.4，库会匹配3.3.x中最新版本。



/*注：babel-runtime 是 dependencies 而不是 devDependencies。

