---

---

# <span id="intro">1 Dashboard介绍</span>

dashboard是商业智能仪表盘的简称，它是一般商业智能都拥有的实现数据可视化的模块，是向企业展示度量信息和关键业务指标（KPI）的数据虚拟化工具。dashboard以丰富的，可交互的可视化界面为数据提供更好的使用体验。

# <span id="todo"> 2 Dashboard能做什么</span>

本产品是自由可拖拽式的Dashboard，采用栅格系统的自由可视化布局，内置了几十种可视化图表组件，支持在线和离线的GIS地图应用，图标之间支持相互交互联动，支持图标的自由定制接入，数据的动态刷新，主题的自由切换，且支持skd的二次开发。

所以本产品具备统计数据和大数据可视化能力、大屏可视化能力、实时数据可视化能力。在阿坝项目、新疆项目的高危人群预警和画像、食药监、五粮液等项目中均有使用。

# <span id="chart"> 3   自定义图表</span>

##  <span id="chartIntro">3.1 自定义图表介绍</span>

自定义图表为自己代码实现方式的组件，相当于dashboard的扩展接口组件，可实现各种图标，如水球图，折线图饼图的混合图等，并且提供接入数据功能，可与其他组件形成联动与被联动关系。

## <span id="whattodo">3.2 自定义图表能做什么</span>

当仪表盘内置图表组件或者内置组件的展示方式不符合需求的时候，可根据需要按照开发手册写出自己想要的图表，并且实现想要的图表逻辑和展示方式。

## <span id="howDev">3.3 如何开发一个图表</span>

1、打开dashboard界面，拖拽左边自定义图表组件进入中间画布区域。

![image002 (1)](https://raw.githubusercontent.com/turingsoul/XDT-DOC/master/xdt/devDoc/_book/img/image002%20(1).jpg)

2、选中画布区域的自定义组件。

3、在组件左边根据需要配置数据源(可以不配置)

4、定义数据源，并且点击获取数据按钮，(ps:缓存数据查询)。如不需要绑定数据，可不用填写。



![image004](https://raw.githubusercontent.com/turingsoul/XDT-DOC/master/xdt/devDoc/_book/img/image004.jpg)

5、切换到样式选项，查看或者编写自定义代码。下面是一个自定义折线图的代码解析

![image006](https://raw.githubusercontent.com/turingsoul/XDT-DOC/master/xdt/devDoc/img/image006.jpg)

6、点击立即执行（重要），此时代码运行并且代码保存到数据中；

##  <span id="case">3.4 案例：水球图</span>

![image008](https://raw.githubusercontent.com/turingsoul/XDT-DOC/master/xdt/devDoc/img/image008.jpg)

 

在当前选中的自定义图表的自定义代码中写入

a)         如需获取数据，则加入获取数据代码

```
//data是获取的数据
var data = this.cfg.chartDefinition.data;
if(!data || !data.resultset){
    return false;
}
```

b)         获取当前的echarts插件并且设置为全局属性(因为引入的水球图插件需要使用全局的echarts对象)

```
//dashboard内置echarts，用按如下方式使用：
var echarts = arguments[0];
window.echarts = echarts;
```

c)         引入水球图的插件，并保存在变量one中

```
//引入水球图插件
var one = Dashboard.queryAction.getScriptOne({
    name:"liquidfill",
    src:'http://echarts.baidu.com/resource/echarts-liquidfill-1.0.4/dist/echarts-liquidfill.js'
});
```

d)         重置echarts实例

```
var echartsInstance = this.echartsInstance || echarts.init(this.htmlObj);
echartsInstance.dispose();
echartsInstance = echarts.init(this.htmlObj);
```

e)         定义echarts所需option

```
var option = {
    series:[{
        type:'liquidFill',
        radius:'80%',
        data:[0.5,0.45,0.4,0.3],
        label:{
            normal:{
                textStyle:{
                    color:'red',
                    insideColor:'yellow',
                    fontSize:50
                }
            }
        }
    }]
}
```

f)          当插件加载完成时就渲染图表

```
one.then(function(){
    echartsInstance.setOption(option);
});
```

g)         编写resize代码

```
this.resize = function(){
    echartsInstance.clear();
    echartsInstance.resize();
    echartsInstance.setOption(option);
}
```

## 3.5<span id="caseCode"> 案例代码</span>

```
//data 是 获取的数据

var data = this.cfg.chartDefinition.data;

if (!data || !data.resultset) {

    return false;

}

//dashboard 内置echarts ，用按如下方式使用；

var echarts = arguments[0];

window.echarts = echarts;

//引入水球图插件

var one = Dashboard.queryAction.getScriptOnce({

    name: 'liquidfill',

    src: 'http://echarts.baidu.com/resource/echarts-liquidfill-1.0.4/dist/echarts-liquidfill.js'

});

var option = {

    series: [{

        type: 'liquidFill',

        radius: '80%',

        data: [0.5, 0.45, 0.4, 0.3],

        label: {

            normal: {

                textStyle: {

                    color: 'red',

                    insideColor: 'yellow',

                    fontSize: 50

                }

            }

        }

    }]

};

var echartsInstance = this.echartsInstance || echarts.init(this.htmlObj);

echartsInstance.dispose();

echartsInstance = echarts.init(this.htmlObj);

 

this.resize = function() {

    echartsInstance.clear();

    echartsInstance.resize();

    echartsInstance.setOption(option);

};

one.then(function(){

    echartsInstance.setOption(option);

});
```

