告别吃土，发现白菜。帮你剁手帮你买。

这是一个自动监控商品价格的项目
目前只做了amazon


#usage

```
git clone git@github.com:chenminhua/amazon.git
cd amazon
cp amazon /usr/local/bin/amazon
```

然后用crontab起一个定时任务

```
crontab -e
```

在打开的文件中写上

```
0 6 * * * /usr/local/bin/amazon LL16 https://www.amazon.cn/gp/product/B00M6OSG40/
```

上面的例子会为我在每天六点的时候更新该商品的价格，你也可以设定其他的频率。
注意要自己填上商品名和商品url

价格在~/.amz_product/目录下的文件中

#get informed

每天去cat这些文件实在太麻烦了
我们可以在.bashrc或者.zshrc中加上如下代码

```
Folder="$HOME/.amz_product/"
for file in `ls ${Folder}`
do
	echo $file
	tail -1 $Folder/$file
done
```

这样以后每次开terminal或者新建一个iterm的tab的时候都会看到你想买的东西的当前价格

![screen](https://github.com/chenminhua/amazon/blob/master/screen.png)

每天都能看到自己想要的东西，是不是感觉自己穷穷哒，是不是学习工作又充满了动力。


#todo
其实可以考虑每天给自己发邮件，或者设置触发事件给自己发邮件，
或者使用系统通知（看到一个叫node-notifier的项目不错，有兴趣的可以用node改写）
代码很简单，如果您觉得好用，直接拿走就好。如果您有更好的idea愿意告诉我，再好不过。




