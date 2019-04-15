# Git Learning 廖雪峰

## 创建版本库

``` 
$ git init
```

```
$ git add file
```

``` 
$ git commit -m "The change in this commitment"
```

## 版本控制

### 查看日志

``` 
$ git log 
```

可选参数一栏显示

```
$ git log --pretty=oneline
```

### 回退版本

利用HEAD表示当前版本，HEAD^ 表示上一个版本，HEAD^^ 表示上上个版本，HEAD~100 表上上100个版本

示例

```
$ git reset --hard HEAD^
```

