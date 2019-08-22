## **一、Maven POM(Project Object Model)**

**POM中可以指定以下配置：**

- 项目依赖
- 插件
- 执行目标
- 项目构建profile
- 项目版本
- 项目开发者列表
- 相关邮件列表信息

**POM文件都需要的project元素，三个必须元素和两个非必须元素：**

- project：工程根标签
- groupId(必须)：命名方式与java包名的表示方式类似，通常与域名反向一一对应
- artifactId(必须)：定义实际项目中的一个Maven项目(模块)，推荐使用实际项目名称作为artifactId的前缀
- version(必须)：定义Maven项目当前所处的版本
- packaging(非必须)：定义Maven项目的打包方式，如jar、war，默认为jar包，打包方式会影响到构建的生命周期
- classifier(不能直接定义)：用来帮助定义构建输出的一些附属构件

**父（Super）POM**

- 父（Super）POM是 Maven 默认的 POM。所有的 POM 都继承自一个父 POM（无论是否显式定义了这个父 POM）。父 POM 包含了一些可以被继承的默认设置。因此，当 Maven 发现需要下载 POM 中的 依赖时，它会到 Super POM 中配置的默认仓库 http://repo1.maven.org/maven2 去下载。
- Maven 使用 mvn help:effective-pom（Super pom 加上工程自己的配置）来执行相关的目标，它帮助开发者在 pom.xml 中做尽可能少的配置，当然这些配置可以被重写。

## **二、Maven构建生命周期**

![img](C:/Users/easysir/AppData/Local/YNote/data/easysir10@163.com/fa7354197d03455cae14378a645eee6a/clipboard.png)

1. **Clean生命周期：项目的清理的处理**

当我们执行mvn post-clean 命令时，Maven 调用 clean 生命周期，它包含以下阶段：

- pre-clean：执行一些需要在clean之前完成的工作
- clean：移除所有上一次构建生成的文件
- post-clean：执行一些需要在clean之后立刻完成的工作

2. **Default (Build) 生命周期：项目部署的处理**

Default (Build) 生命周期是Maven的主要生命周期，被用于构建应用。

3. **Site 生命周期：项目站点文档创建的处理**

Maven Site 插件一般用来创建新的报告文档、部署站点等。

- pre-site：执行一些需要在生成站点文档之前完成的工作
- site：生成项目的站点文档
- post-site： 执行一些需要在生成站点文档之后完成的工作，并且为部署做准备
- site-deploy：将生成的站点文档部署到特定的服务器上

## **三、Maven依赖管理**

**依赖的基本坐标gav：**

- groupId
- artifactId
- version

**依赖类型type：**

- 依赖的类型，对应于项目坐标定义的packaging
- 默认值为jar

**依赖的范围scope：**

![img](C:/Users/easysir/AppData/Local/YNote/data/easysir10@163.com/4e615c1acc2f44e9998e34e3b1a7b097/1546244402969.png)

**标记依赖是否可选：**

- optional

**排除传递性依赖：**

- exclusions
- 当声明exclusions时只需要groupId和artifactId，不需要version元素

**依赖调节：**

- 第一原则：路径最近者优先
- 第二原则：第一声明者优先

## **四、Maven仓库**

![img](C:/Users/easysir/AppData/Local/YNote/data/easysir10@163.com/46da95cc4e7b4647919eb17caa5093ff/1546256506707.png)

**Maven依赖搜索顺序：**

1. 搜索本地仓库
2. 搜索远程仓库
3. 若均没有所需构件，Maven报错