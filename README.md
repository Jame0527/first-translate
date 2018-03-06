# prettier 中文文档 
## 尝试去写一些文档的翻译 但是英语水平也是有点low 有什么不足之处 多多指教
## 不去介绍prettier 应该都知道是干什么的  只要试着去翻译下cli 
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
   > console.log(./my/.prettierrc)
   ##### --ignore-path
    都有些见不得人的东西 git可以通过.gitignore忽略不上传的文件 prettier也一样 也可以通过--ignore-path 去指定哪些文件见不得人（跳过格式化） 但是正常人的做法是跟git一样根目录新建.prettierignore文件
    也可以在代码中添加prettier-ignore的注释的标识 跳过某一段代码块 具体操作可以看demo

   ##### --require-pragma
    感觉这个玩意就是跟别人说：“来 干我啊” prettier 会优先处理添加了@prettier注释头的文件
   ##### --insert-pragrma 
    这是给--require-pragma 充当先锋的东西  可以为指定文件的头部添加@format注释头
   ##### --list-different
    检测哪些文件是和prettier设定的格式化配置不一样的  会打印出不一样的文件名 但是直接运行命令行只会输出不一样的文件名 但是写在script 如果只要检测到不一样的文件 会直接报错 
   ##### --no-config
    这个应该都明白了  忽略配置文件  直接使用prettier默认配置文件
   ##### --config-precedence
    设置prettier 以哪种方式进行format  
   > cli-override(默认prettier cli的形式format文件)
   >
     例如：通过config 指定了.prettierrc配置文件 但是运行的时候命令行中添加了options的cli的指令 prettier会忽略.prettierrc配置文件 按照cli指令去format文件
   > file-override 
     配置文件权重高于cli指令 
   >   
   > prefer-override 
     会优先查找.prettierrc配置文件 查找不到在执行cli指令
   ##### --no-editorconfig

   ##### --with-node-modules
    忽略node_modules文件夹
   ##### --write
    和eslit --fix相同 意思就是按照规定的格式对文件进行重写
   ##### --loglevel
    不想翻译这个东西

prettier options （1.7.1版本运行有问题 ）
=====================================================
   ##### Print Width 
   换行的长度 在配置文件中要遵循驼峰命名法 如果你format makedown的文件不想换行 可以使用Prose Wrap禁止
   > 默认是 80 cli设定方式： --print-width <int> 或者调用api printWith:<init>
   ##### Tab Width
    每次写代码都纠结于两个空格还是4个空格
   > 默认是 2 cli设定方式： --tab-width <int> 或者调用api tabWidth:<init>
   ##### tabs 
   利用空行符替换空格缩进  不建议使用  默认是false cli设定： --use-tabs api：useTabs:<bool>
   #####    Semicolons
   要不要分号呢 true 要 false 不要 defind true cli: --no-semi  api：semi: <bool>
   ##### Quotes
   单引号代替双引号? defind false; cli: --single-quotes api: singleQuotos: <bool> 
   ##### Trailing commas 
   尾随逗号 例如 object的最后一个key-value是否要加逗号 
   > 三个值可供挑选
   > none 不会添加分号
   > es5 对象 数组最后一项在换行时会添加分号 单行是不会添加的
   > all 能加的都加上包括函数的不定参  但是需要node版本在8以上或者bable的transform (个人不建议使用)
  ##### Bracket Spacing
  > 在对象两边是否打印空格
  > 默认是true cli: --no-bracket-spacing api: bracketSpacing: <bool>
  ##### JSX Brackets
  > 多行jsx >结束符在文件的下一行而不是结尾（自闭标签除外）
  > 默认false cli --jsx-bracket-same-line api: jsxBracketSameLine: <bool>
  ##### Arrow Function Parentheses
  > 箭头函数参数是否要添加括号
  > avoid: 默认值  尽量省略括号
  > always: 添加括号
  ##### Rang
  > 格式化部分文件 
  > 通过配置两个参数来格式化部分代码（感觉这个东西有毒）
  > range-start <init> 默认 0 cli: --range-start <init> api: rangeStart: <int>
  > range-end <init> 默认 Infinity cli:--range-end <init> api: rangeEnd: <init>


























