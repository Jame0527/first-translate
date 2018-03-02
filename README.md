# prettier 中文文档 
## 尝试去写一些文档的翻译 但是英语水平也是有点low 有什么不足之处 多多指教
## 不去介绍prettier 应该都知道是干什么的  只要试着去翻译下cli 跟api
install
=====================================
### prettier 同时支持yarn 和 npm
   #### yarn 安装方式如下（感觉这点就是凑数的~）
    yarn add prettier --dev --exact
    或者全局安装
    yarn global add prettier
   #### npm 安装方式如下
    npm install --save-dev --save-exact prettier
    或者全局安装
    npm install --global prettier   
prettier cli
=====================================
#### 你可以使用script 定义命令行去运行prettier 也可以去通过定义option运行prettier 
   ##### 先介绍cli 
   >当你想在提交代码之前格式化本地代码 可以使用 --write 示例如下 
   prettier [opts] [filename ...]
   > prettier 后边添加cli 最后表明要格式化的文件名称（通常正则去匹配或者写具体的文件名）
   > 官网示例
   prettier --single-quote --trailing-comma es5 --write "{app,__{tests,mocks}__}/**/*.js"
   ##### --debug-check
   会输出你要格式化代码的名称 可以去prettier-demo里边尝试一下  prettier其实原理就是改写你要格式化代码的文件，但是可能在格式化完成之后代码会出现问题 所以在--write之前可以看下要格式化的文件有哪些
   再去判断要不要执行--write;
   >需要注意的是 --write 和 --debug-check 不能一块执行
   ##### --find-config-path and --config

   >--config 意思就是给*.{xxxxx}文件找了个媳妇 但是只有它自己知道 相反--find-config-path 就是让其他人知道*.{xxxxx}文件的媳妇是谁 
   >
   > prettier --config ./my/.prettierrc --write ./my/file.js
   >
   > prettier --find-config-path ./my/file.js
    >./my/.prettierrc
   ##### --ignore-path
    都有些见不得人的东西 git可以通过.gitignore忽略不上传的文件 prettier也一样 也可以通过--ignore-path 去指定哪些文件见不得人（跳过格式化） 但是正常人的做法是跟git一样根目录新建.prettierignore文件
    也可以在代码中添加prettier-ignore的注释的标识 跳过某一段代码块 具体操作可以看demo

   ##### --require-pragma
    感觉这个玩意就是跟别人说：“来 干我啊” 但是可以增加代码的可读性 起码一看文件开头就知道这个文件被修理过
























