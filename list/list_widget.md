# 遍历List Widget
最直接的方法如下：

```python
items = []
for index in xrange(self.listWidget.count()):
     items.append(self.listWidget.item(index))
```
但是这样很不pythonic，基于一般越短的代码就是越正确的代码的原理，可以像下面这样：

```python
all_items = self.listWidgetA.findItems(QString('*'), Qt.MatchWrap | Qt.MatchWildcard)
```
但是这相当于把所有的items全部存到一个list里面了，会费资源，还是不好。

可以考虑如下方式，在listWidget的subclass里定义一个iterAllItems method,其实他是一个generator。

```python
def iterAllItems(self):
    for i in range(self.count()):
        yield self.item(i)
```

