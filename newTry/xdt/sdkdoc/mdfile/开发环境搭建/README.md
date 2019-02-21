# 开发环境搭建

&ensp; &ensp;&ensp;Dashboard提供SDK包，通过SDK包提供的组件和API，用户可以快速构建页面或者应用。

+ **步骤1 获取SDK包，下载SDK包至本地。**

+ **步骤2 将SDK包解压，解压后结构如下：**

    ├─ sdk

    ├─   ├─ resource

    ├─   ├─ dashboard.core.js

    ├─   ├─ styles.css

    resource：SDK包资源文件夹，包含图片、字体文件等。

    dashboard.core.js：SDK包主文件。

    styles.css：SDK包样式文件。

+ **步骤3 在项目中引入js和css文件，如下：**

````html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>my app</title>
    <link rel="stylesheet" href="./sdk/styles.css">
</head>
<body>
    <div id="app"></div>
    <script src="./sdk/dashboard.core.js"></script>
    <script>
    //code...
    </script>
</body>
</html>
````


+ **步骤4 通过SDK提供的组件和API开发页面。**

+ **步骤5 开发环境构建完成。**