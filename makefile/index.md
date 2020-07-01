# Makefile 确实是个好用的东西


博客使用hugo + GitHub hosting 有各种需要执行的命令，及其繁琐。 但是有了Makefile的话，事情就简单了很多。 

封装常用的命令，然后make *  enjoy your self 

附上博客现在用的Makefile: 

```
build:
	hugo

# 在posts目录下创建新的文章，并使用默认的md编辑器打开
.PHONY: new
new:
	hugo new posts/${path} && open content/posts/${path}

.PHONY: delete
delete:
	rm -rf content/posts/${path}

# 发布至me-jser（submodule）
.PHONY: publish
publish: 
	cd me-jser.github.io && git add . && git commit -m '${msg}' && git push origin master

# 提交主项目代码
.PHONY: commit
commit: 
	git add . && git commit -m '${msg}' && git push origin master
```



