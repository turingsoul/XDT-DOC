# 案例：水球图

![image008](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image008.jpg)

在当前选中的自定义图表的自定义代码中写入

a)         如需获取数据，则加入获取数据代码

```
var data = this.cfg.chartDefinition.data;

​	   if(!data||!data.resultset){ 

​		return false;

   }
```

![image009](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image009.png)

b)         获取当前的echarts插件并且设置为全局属性(因为引入的水球图插件需要使用全局的echarts对象)

![image010](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image010.png)

c)         引入水球图的插件，并保存在变量one中

![image012](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image012.jpg)

d)         重置echarts实例

![image014](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image014.jpg)

e)         定义echarts所需option

![image016](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image016.jpg)

f)          当插件加载完成时就渲染图表

![image018](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image018.jpg)

g)         编写resize代码

![image019](E:\gitdoc\XDT-DOC\xdt\devDoc\img\image019.png)