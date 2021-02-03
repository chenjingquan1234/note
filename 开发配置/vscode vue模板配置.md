## 1，安装一个插件，识别vue文件

插件库中搜索Vetur，点击安装，安装完成之后点击重新加载

## 2，新建代码片段

文件-->首选项-->用户代码片段-->点击新建代码片段--取名vue.json 确定

## 3，删除不要的代码,粘入自己写的.vue模板

注意模板文件中想缩进的地方不可以使用TAB，必须替换成空格；

```javascript
{
	// Place your snippets for vue here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	"Print to console": {
		"prefix": "vue",
		"body": [
			"<!-- $1 -->",
			"<template>",
			"  <div class='$2'>$5</div>",
			"</template>",
			"",
			"<script>",
			
			"export default {",
			"  components: {},",
			"  data() {",
			"    return {",
			"        ",
			"    };",
			"  },",
			"  //监听属性 类似于data概念",
			"  computed: {},",
			"  //生命周期 - 挂载完成（可以访问DOM元素）",
			"  mounted() {",
			"      ",
			"  },",
			"  //监控data中的数据变化",
			"  watch: {},",
			"  ",
			"  methods: {",
			"      ",
			"  },",
			"  destroyed() {}, ",
			"}  ",
			"</script>",
			"    ",
			"<style lang='' scoped>",
			"    $4",
			"</style>"
		],
		"description": "Log output to console"
	}
}
```

## 5，重启vscode;

上面代码中的 "prefix": "vue", 就是快捷键；保存好之后，新建.vue结尾的文件。这时新建的vue是空白文件。在此空白文件中输入vue + tab，会自动加载自定义的vue模板；