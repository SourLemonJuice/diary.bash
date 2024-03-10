# 日记创建脚本(linux.bash)

## 1.自述

这是我写的第一个有实际作用的`bash`脚本哦

用来在一个文件夹里以固定的命名规则创建文本文件，也就是所谓的日记\
我其实早就不用它了，毕竟写它有什么意义呢，都一样

不管怎么说，一个一直陪着我学习 linux 和 bash 的git储存库对我来说还是很有价值的，所以做点修改加一个自述文件就上传上来啦

## 2.配置

作为配置项的变量都定义在脚本的顶部，真正需要改的应该是这些地方

```bash
#文件们应该都放在哪里
FilePath="./"
#要使用的文本编辑器
# 可以正常释放参数，比如 "vim --opt"
# 不过请注意启动编辑器时使用的是 exec 命令，emm...不要搞出注入'攻击'就好，比如以 "-a xxx, -c, -l" 开头，详细参数可以执行 $(exec --help) 查看
# 脚本会将文件路径接在字符串的最后面，比如 "vim --opt /file.txt"
EditorExec="vim"
#新文件的权限
NewFilePermission="644"
```

尤其是`FilePath`它是储存所有文件的目录，其结构类似这样

```text
${FilePath}
├── date1.txt
└── date2.txt
```

`EditorExec`则为启动编辑器的命令，要编辑的文件路径会被加在命令的最后，也只能加在最后\
`NewFilePermission`是创建文件的权限`chmod $NewFilePermission "$FileLocation"`