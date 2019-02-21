# API

<h2 id="框架API">框架API</h2>

<br/>

### [属性](#)

<br/>

#### version | 【 String 】

dashboard版本

<br/>

#### util | 【 Object 】 

平台提供的工具函数集合。

<br/>

#### lib | 【 Object 】 

平台提供的库类。

<br/>

#### lib.$ | 【 Object 】 

jQuery库，高效精简，功能丰富的JavaScript工具库。

<br/>

#### lib._ | 【 Object 】 

underscore库，是一个JavaScript使用库，提供一整套函数式编程的实用功能。

<br/>

#### widgetBaseClass | 【 Object 】 

组件基类，所有组件实现需继承此基类。

<br/>

### [方法](#)

<br/>

#### bootstrap(cb)

SDK引导程序。

+ **参数**

    cb | Function 回调函数

+ **返回值**

    【Promise】

<br/>

#### register(name,options,isCustom)

注册组件。

+ **参数**

    name | 【 String 】

    组件类型

    options | 【Object】

    参数对象 {widgetClass,widgetConfig}

    isCustom | 【Boolean】

    是否自定义组件

+ **返回值**

/

<br/>

#### add(options)

添加组件

+ **参数**

+ options | 【Object】

    参数对象

    options.htmlObj | 【DOM Object】 

    组件添加的位置

    options.cfg | 【Object 】

    组件的config对象

+ **返回值**

    【Object】组件实例对象

<br/>

#### remove(id)

移除组件

+ **参数**

    id | 【 String 】

    组件ID

+ **返回值**

/

<h2 id="组件基类API">组件基类API</h2>

<br/>

### [属性](#)

<br/>

#### allowQueryErrorCount | 【 Number 】 

数据源刷新，最大允许错误次数。

<br/>

#### cfg | 【 Object 】

组件配置

<br/>

#### cfg.bigandsmall | 【 Boolean 】

是否支持放大/缩小

<br/>

#### cfg.chartBtns | 【 Boolean 】

（图表属性）是否显示图表的功能键

<br/>

#### cfg.chartDefinition | 【 Object 】

关于图表的定义

<br/>

#### cfg.chartDefinition.data | 【 Object 】

数据

<br/>

#### cfg.chartDefinition.defaultOption | 【 Object 】

(图表属性)默认option

<br/>

#### cfg.chartDefinition.hasFreshQuery | 【 Boolean 】

(组件属性)是否刷新数据源

<br/>

#### cfg.chartDefinition.freshQuery | 【 Boolean 】

(图表属性)是否刷新数据源

<br/>

#### cfg.chartDefinition.id | 【 String 】

组件配置id

<br/>

#### cfg.chartDefinition.inject | 【 Object 】

注入代码

<br/>

#### cfg.chartDefinition.option | 【 Object 】

配置option

<br/>

#### cfg.chartDefinition.query | 【 String 】

数据源

<br/>

#### cfg.chartDefinition.queryid | 【 String 】

数据源id

<br/>

#### cfg.chartDefinition.queryname | 【 String 】

数据源名称

<br/>

#### cfg.executeAtStart | 【 Boolean 】

执行时启动

<br/>

#### cfg.id | 【 String 】

组件id

<br/>

#### cfg.layout | 【 Object 】

组件的布局

<br/>

#### cfg.listeners | 【 Object 】

被监听的参数

<br/>

#### cfg.name | 【 String 】

组件名称

<br/>

#### cfg.type | 【 String 】

组件类型

<br/>

#### echartsDom | 【 Object 】

echart实例

<br/>

#### htmlObj | 【 DOM Object 】

容器

<br/>

#### id | 【 String 】

组件id

<br/>

#### isEditMode | 【 Boolean 】

是否处于编辑模式

<br/>

#### isFirstQuery | 【 Number 】

数据源获取次数。

<br/>

#### loader | 【 Object 】

加载图，被创建后有hide与show两种状态

<br/>

#### minFreshPeriod | 【 Number 】

数据源刷新最小时间，单位：秒

<br/>

#### oldTime | 【 Number 】

上一次组件刷新时间

<br/>

#### queryErrorCount | 【 Number 】

数据源错误次数。

<br/>

#### queryState | 【 String 】

数据源获取状态。

<br/>

#### rawhtmlObj | 【 DOM Object 】

容器

<br/>

#### resizeState | 【 string 】

组件实例刷新状态

<br/>

#### rootDom | 【 DOM Object 】

容器

<br/>

#### tickIsStop | 【 Boolean 】

是否停止刷新。

<br/>

### [方法](#)

<br/>

#### setContainerDom()

在htmlObj下设置一个新的div 作为组件容器。

+ **参数**

/

+ **返回值**

/

<br/>

#### createLoader()

创建加载图，返回对它状态控制的对象。

+ **参数**

/

+ **返回值**

【Object】

<br/>

#### setParameter(value)

具有parameter属性的组件中，当值变化时，触发该方法，改变globalParam中相应的值。

+ **参数**

    value | 【 * 】

    属性值

+ **返回值**

【Object】

<br/>

#### getParameter(parameterid)

获取globalParam中该属性的值。

+ **参数**

    parameterid | 【 String 】

    属性id

+ **返回值**

【*】

<br/>

#### paramListenedChange(obj1,obj2)

监听参数变化，通知组件接口

+ **参数**

    obj1 | 【 Object 】

    listeners 中 监听有改变的参数

    obj2 | 【 Object 】

    所有改变的参数

+ **返回值**

/

<br/>

#### setFreshPeriod(time)

设置数据源刷新时间。

+ **参数**

    time | 【 Number 】

    刷新时间

+ **返回值**

/

<br/>

#### setTickState(state)

设置数据源刷新状态。

+ **参数**

    state | 【 Boolean 】

    刷新状态

+ **返回值**

/

<br/>

#### freshTick()

刷新数据源

+ **参数**

/

+ **返回值**

/

<br/>

#### doQuery(callback,initor)

查询数据

+ **参数**

    callback | 【 Function 】

    回调函数

    initor | 【 * 】

    触发原因

+ **返回值**

/

<br/>

#### queryFetched(data)

数据获取回来的钩子，子类继承这个钩子

+ **参数**

    data | 【 * 】

    数据

+ **返回值**

/

<br/>

#### paramChanged(obj)

参数改变后的钩子，子类继承这个钩子

+ **参数**

    obj | 【 object 】

    参数对象

+ **返回值**

/

<br/>

#### widgetWillCreated(cfg)

组件创建前触发该函数，子类继承这个钩子

+ **参数**

    cfg | 【 Object 】

    组件配置

+ **返回值**

/

<br/>

#### widgetDidCreated(cfg)

组件创建前触发该函数，子类继承这个钩子

+ **参数**

    cfg | 【 Object 】

    组件配置

+ **返回值**

/

<br/>

#### preUpdate(nextCfg)

组件创建前触发该函数，子类继承这个钩子

+ **参数**

    nextCfg | 【 Object 】

    变化后的组件配置

+ **返回值**

/

<br/>

#### update(nextCfg)

更新组件

+ **参数**

    nextCfg | 【 Object 】

    变化后的组件配置

+ **返回值**

/

<br/>

#### postUpdate(nextCfg)

组件更新后触发该函数，子类继承这个钩子

+ **参数**

    nextCfg | 【 Object 】

    变化后的组件配置

+ **返回值**

/

<br/>

#### resize()

window resize 触发该函数

+ **参数**

/

+ **返回值**

/

<br/>

#### draw()

绘制组件

+ **参数**

/

+ **返回值**

/

<br/>

#### handleData()

处理数据

+ **参数**

/

+ **返回值**

/

<br/>

#### destroy()

销毁组件

+ **参数**

/

+ **返回值**

/

<br/>

#### getCfg()

获取配置

+ **参数**

/

+ **返回值**

【Object】组件配置对象

<br/>