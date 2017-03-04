# myCodeMirror
开发一个线上的编辑js的工具，可以实时预览，输出想要的结果

#开发教程
CodeMirror是一款在线的支持语法高亮的代码编辑器。官网： (http://codemirror.net)
1.首先下载codemirror的安装包，将lib目录下的文件 codemirror.css 和 codemirror.js 拷入到项目中

```
<!DOCTYPE html>
<html>
<head>
  <title>在线编辑器</title>
  <script src="lib/codemirror.js"></script>
  <link rel="stylesheet" href="lib/codemirror.css">
</head>
<body>
</body>
</html>

```
2. 接下来要引用的就是在mode目录下编辑器中要编辑的语言对应的js文件，下面以js文件为例:

```
<script src="mode/javascript/javascript.js"></script>
```
3.执行一下js脚本
```
<!DOCTYPE html>
<html>

<head>
  <title>在线编辑器</title>
  <script src="lib/codemirror.js"></script>
  <link rel="stylesheet" href="lib/codemirror.css">
</head>

<body>
  <textarea id="eidor"></textarea>
  <script src="mode/javascript/javascript.js"></script>
  <script>
    var myCodeMirror = CodeMirror(document.getElementById('eidor'), {
      lineNumbers: true
    });
  </script>
</body>

</html>
```
# 添加theme样式
```
 var el = document.getElementById('eidtor')
    var selectEl = document.getElementById('select') 
    var myCodeMirror = CodeMirror(el, {
      value: "function myScript(){return 100;}",
      mode: "text/javascript",
      lineNumbers: true,
      theme: 'solarized dark',
      indentUnit: 2,
      smartIndent: true,
      tabSize: 2,
    });

    // 监听select变化 改变 code 的 theme (主题)
    selectEl.addEventListener('change', function(){
      var fileName = selectEl.options[selectEl.selectedIndex].innerText
      var link = document.createElement('link')
      link.rel = 'stylesheet'
      link.type = 'text/css'
      link.href = 'theme/'+ fileName +'.css'
      document.head.appendChild(link);
      myCodeMirror.setOption('theme', fileName)
    })
```

# 参考文档
[在线代码编辑器 CODEMIRROR 配置说明](http://www.hyjiacan.com/codemirror-config/)
