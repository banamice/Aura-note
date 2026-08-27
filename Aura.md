# Aura

## 背景介绍

 包含 GAS 系统    MVC架构   数据驱动    AI行为树     网络数据同步多人联机   存档系统





# 编辑器设置

## 设置Aura蓝图项目使用UE编辑器版本

右键 uproject 会有一个switch unreal engine version  选择之后才能打开  并且由于是一个蓝图项目本身 所以需要先打开创建一个C++类之后才能用rider进行代码编辑



## 设置编辑器IDE

IDE用的是RIDER

![10018304-25fb-416d-9418-68523e63fae3](./images/10018304-25fb-416d-9418-68523e63fae3.png)

### RIder和 Rider ubject的区别



## 项目设置

### 关闭了live coding

![1c44ab07-6bc0-4750-90a1-649f061d39b5](./images/1c44ab07-6bc0-4750-90a1-649f061d39b5.png)

### 关闭自动编译添加的C++类功能

![086bae94-d645-4cf0-84e1-69868b7f1d2c](./images/086bae94-d645-4cf0-84e1-69868b7f1d2c.png)



### 在插件里开启RIDER集成插件

![4b84c0dc-a994-4780-a305-0ddc78a30a38](./images/4b84c0dc-a994-4780-a305-0ddc78a30a38.png)

### 把版权声明设置为空

这样头文件和Cpp就不会每次在·文件顶都有注释了

![c6df9532-83a9-405c-96c7-13e576f77e17](./images/c6df9532-83a9-405c-96c7-13e576f77e17.png)

### 设置新开窗口打开位置为主窗口边上

这样每次打开资源都会像浏览器tag一样 不用手动托了

![1d3f0fd7-fb5c-4516-9739-b38ba02c6dca](./images/1d3f0fd7-fb5c-4516-9739-b38ba02c6dca.png)



## UE5.8设置

由于是使用的5.8

RIDER在预览build.cs的时候会报错  虽然不影响编译但是看着很难受

```
“System.Collections.Generic.List<T>”在未引用的程序集中定义。必须添加对程序集“mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”的引用。
无法解析符号'string'
类型“System.Collections.Generic.List<T>”在未引用的程序集中定义。必须添加对程序集“mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”的引用。
无法解析符号'string'
```

AI是这么说的

```
Rider 中 UE5 Build.cs 文件报错问题分析与解决
这是一个非常常见的 Rider + UE5 的 C# 智能提示/解析配置问题，根本原因是 Rider 的 C# 语言服务（Roslyn）无法正确识别 UBT（Unreal Build Tool）使用的 .NET 运行时和程序集引用。
让我先查看一下您的项目配置：根据您的描述和我对项目的分析，这是一个 Rider IDE 中针对 UE5 .Build.cs 文件的已知问题，与实际编译无关，纯粹是 IDE 的代码分析/解析问题。

问题原因
这个错误：
"类型 System.Collections.Generic.List  在未引用的程序集中定义，必须添加对 mscorlib 的引用" "无法解析符号 string" 
是因为 Rider 在分析 .Build.cs 文件时，没有正确找到对应的 .NET SDK/Framework 程序集，导致连最基础的 string、List<T> 类型都无法解析。.Build.cs 文件由 UE5 的 UnrealBuildTool 使用，它是一个独立的 C# 项目，Rider 需要正确配置才能分析它。

解决方案（按推荐顺序尝试）
✅ 方法一：安装 .NET SDK（最常见原因）[1]
Rider 2024+ 版本需要 .NET 8 或 .NET 10 SDK 来解析 Build.cs 文件，而不依赖旧的 mscorlib。
前往 https://dotnet.microsoft.com/download
下载并安装 .NET 8 SDK 或 .NET 10 SDK（推荐 LTS 版本）
安装完成后重启 Rider
```

直接下了.NET10安装就好了



# 设置版本管理

课程中是使用了git bash然后手动配置 .gitignore 也没有使用lfs的方式来上传资源文件

我会记录我自己的方法

详情可以参考 

[banamice/git-and-RiderAiSet-Note: 关于如何使用rider ai以及 git基础 如何在UE5+Rider环境使用git 建议搭配隔壁测试UE5.8GitTest项目食用](https://github.com/banamice/git-and-RiderAiSet-Note)



这里只是做了简要介绍

## 创建github仓库

创建好仓库后

我是使用gitbash 配置了global ssh  所以使用ssh方式配置远程仓库

![a4e54368-1b25-4ad7-9e66-81a8f519750c](./images/a4e54368-1b25-4ad7-9e66-81a8f519750c.png)

```
git remote add origin git@github.com:banamice/GasAbilitySystem_Aura.git
git branch -M main
git push -u origin main
```





## 创建一个c++类好让rider可以打开ide

这里随便创建就好

![f1e2af9c-294e-483a-ae5c-12cc4b1aca45](./images/f1e2af9c-294e-483a-ae5c-12cc4b1aca45.png)

创建完成之后 打开rider

![ca3f558e-8583-471e-8d00-4683b57482f5](./images/ca3f558e-8583-471e-8d00-4683b57482f5.png)

### 打开时遇到了如下报错

```
13:53:00.311: dotnet.exe "E:\UE5\UE_5.8\UE_5.8\Engine\Binaries\DotNET\UnrealBuildTool\UnrealBuildTool.dll" -ProjectFiles -Rider -Automated -OnlyPrimaryProjectFile -Minimize -NoMutex -Log=C:\Users\banannice\AppData\Local\JetBrains\Rider2026.2\log\UBT_GPF.txt E:\UE5\projects\Aura\Aura\Aura.uproject
13:53:00.341: You must install or update .NET to run this application.
13:53:00.342: App: E:\UE5\UE_5.8\UE_5.8\Engine\Binaries\DotNET\UnrealBuildTool\UnrealBuildTool.dll
13:53:00.342: Architecture: x64
```

我之前都是直接生成的C++项目还没遇到过这种情况



解决方案为

```
🛠️ 解决方案（按顺序尝试）
方案 1：重新生成项目文件（最常见问题）
蓝图项目转 C++ 后，必须先生成 .sln 解决方案文件，Rider 才能正确加载。
找到您的 .uproject 文件：Aura.uproject
右键点击 Aura.uproject
选择 "Generate Visual Studio project files"（生成 Visual Studio 项目文件）
等待生成完成后，再用 Rider 打开生成的 Aura.sln
```

## 在打开的editor里右下角有这样的设置

![4858b06b-ec8f-4de9-aa2d-b1a5b990edeb](./images/4858b06b-ec8f-4de9-aa2d-b1a5b990edeb.png)   

点开后是这样的一个界面 然后填入信息  最后点init   其实去看.gitattribute文件就可以发现 ue是吧整个content的内容交给了lfs来处理   github免费容量有 10G 应该够了吧

![7d792b56-09f8-49e1-915d-1d8298050693](./images/7d792b56-09f8-49e1-915d-1d8298050693.png)



在rider中将一些rider会生成的文件加入版本管理

![429854cb-165b-4129-a222-c826cb306e2e](./images/429854cb-165b-4129-a222-c826cb306e2e.png)

推送至remote

![06be6017-5c3c-467f-8ea1-0499813c0232](./images/06be6017-5c3c-467f-8ea1-0499813c0232.png)

我觉得不好的点就是看不到进度 别人git bash都能看进度 你一个IDE不能看也太蠢了

![99a8bf3a-e9fd-443f-a12a-bf17aec5c28c](./images/99a8bf3a-e9fd-443f-a12a-bf17aec5c28c.png)







# 第二章

## 基础角色类

正常创建就好

### 需要下载debug调试符号

我下载的时候是有需要把IDER和编辑器都关掉才能下载

需要注意的是 一定要在直接结束进程之前保存好对应的修改



### 创建player 与enemy子类

给base的uclass 加上abstaract修饰符让其成为纯虚类 别实例化

![ceb233b8-71c5-4b11-86d8-f98af49e53f1](./images/ceb233b8-71c5-4b11-86d8-f98af49e53f1.png)



## 设置角色蓝图

### 添加武器网格

![6e6ea44e-f430-4474-8eac-88962bcd269f](./images/6e6ea44e-f430-4474-8eac-88962bcd269f.png)

### 添加武器附着socket

注意法杖是放在左手的



### 挑战

自己捏一下哥布林  并且 所有的敌人应该是从一个基础的enemybp里面出来 这样一些蓝图逻辑和配置都可以不用重复改

![ab4832c3-c893-4382-82fa-9812b33c2b81](./images/ab4832c3-c893-4382-82fa-9812b33c2b81.png)



## 制作动画蓝图

### 对于player来说可以选择固定的骨架来开始做动画蓝图

### 对于enemy来说他们不会使用相同的骨架 所以需要用模板来做动画蓝图

![f350f3c5-ecaf-4fe7-b0b8-e72317f10f42](./images/f350f3c5-ecaf-4fe7-b0b8-e72317f10f42.png)

使用这个通用节点代替 实际的混合空间动画  这样在子类中就只需要给这个节点指定混合动画就好

![356847cf-f3c9-4a80-a2b3-fbb0c4aed76a](./images/356847cf-f3c9-4a80-a2b3-fbb0c4aed76a.png)

然后创建具体子类的时候选择刚刚创建的父类  并选择具体骨架

![72ffee8d-2322-42ee-ae23-6ce558ef4bfa](./images/72ffee8d-2322-42ee-ae23-6ce558ef4bfa.png)



然后再资产重写面板指定资产

![858374c0-25aa-4028-93f8-2284ca12e461](./images/858374c0-25aa-4028-93f8-2284ca12e461.png)

### 挑战

制作弹弓哥布林的蓝图和动画类

![4b77e393-93c3-421a-aaad-c276d9f13951](./images/4b77e393-93c3-421a-aaad-c276d9f13951.png)

## 设置玩家增强输入

没啥好说的。这里只设置了move

需要注意 UE中X代表面向的正方向 Y是角色右侧的正方向





### 挑战

创建controller蓝图  需要从C++类继承

![b5ab09e9-dd5b-4cfd-ab96-6c19eb43d2fa](./images/b5ab09e9-dd5b-4cfd-ab96-6c19eb43d2fa.png)

他这里的文件整理格式是 character负责了模型 player负责了输入



## 设置controlelr 绑定增强输入

需要注意 使用增强输入需要添加model "EnhancedInput"   注意这里是在beginplay初始化的

![82253bb4-fa8e-4a18-8760-6ce6329851f2](./images/82253bb4-fa8e-4a18-8760-6ce6329851f2.png)



增强输入的数据流向大概是： 按键按下 inputlocalplayer接收到->查看其下的context 看将这个输入转换给哪一个iinput action  ->  当ia改变时会通知其绑定的inputCompojnent触发对应的回调

重写setup inutcomponent函数 该函数允许controller绑定IA回调

![40d0a483-ac0d-434e-82b1-c95145cf984c](./images/40d0a483-ac0d-434e-82b1-c95145cf984c.png)

关于这里 为什么知道controller 默认的input component组件是enhanced input

这个其实是可以项目设置的

![86e4945d-34f2-413d-b90b-b74a894cd168](./images/86e4945d-34f2-413d-b90b-b74a894cd168.png)



### 挑战

![3f8c1d17-6c3f-4a26-aef0-40b5e6510921](./images/3f8c1d17-6c3f-4a26-aef0-40b5e6510921.png)

![313108f0-2387-4d5c-aee5-2d3f497972c8](./images/313108f0-2387-4d5c-aee5-2d3f497972c8.png)



## 设置gammode将controller 的chracter连接起来

gamemode使用的是gamemodebase 而不是gamemode 我记得 base好像没有match state之类的

### 挑战

为character设置摄像机和弹簧臂   因为这个其实后面是俯视角的 所以测试直接拿蓝图做做把

![8b56479e-b545-4c5b-a2b5-57278e191e79](./images/8b56479e-b545-4c5b-a2b5-57278e191e79.png)



然后这是个俯视角游戏 。所以摄像机其实是固定不动的 只需要打开跟随加速度方向旋转就好  这里还设置了将角色限制在平面上

![95c512ab-ce71-4cbc-983e-e41efdc34e2e](./images/95c512ab-ce71-4cbc-983e-e41efdc34e2e.png)

## 敌人接口

提供一个可高亮接口

![1158f59c-9bfe-47b1-8a3a-e92e83b928d7](./images/1158f59c-9bfe-47b1-8a3a-e92e83b928d7.png)

实现了两个虚函数

![f9de8f0b-7c13-400e-b86d-7c2fb4997795](./images/f9de8f0b-7c13-400e-b86d-7c2fb4997795.png)

## 通过controller的获取鼠标下objkect的接口来检测是否是可高亮物体

因为每一帧都需要检测 所以直接写到了tick上   我怀疑其实就是做了一个射线检测  需要注意的检测时visibility通道 需要看下mesh本身是不是block visibility

![edcf826f-a6da-477a-b4cb-9b8234f3d51e](./images/edcf826f-a6da-477a-b4cb-9b8234f3d51e.png)

这里有击中判断情况需要处理

![334cc98a-7a15-4dc6-89a7-bedb5d50519c](./images/334cc98a-7a15-4dc6-89a7-bedb5d50519c.png)



### 挑战

![cedced01-de12-4a4b-a78c-5ef32dbec63c](./images/cedced01-de12-4a4b-a78c-5ef32dbec63c.png)

## 后处理高亮

想做到这种效果就需要开启后处理

后处理只会在后处理体积内生效就和ai寻路的mesh volum差不多

需要拖一个在level里

![091fbf4f-6654-459a-91f6-279ebfa8610e](./images/091fbf4f-6654-459a-91f6-279ebfa8610e.png)

设置其影响范围无线

![497810d4-1163-4f44-9a1a-1da415a1f483](./images/497810d4-1163-4f44-9a1a-1da415a1f483.png)



然后其需要设置一个材质来显示模型边缘  素材包里自带了 并且 这个是自定义后处理

![c22cc1da-8adc-4979-95bf-3be33881b0f9](./images/c22cc1da-8adc-4979-95bf-3be33881b0f9.png)

关于原理和具体怎么做可以自己去查一下

需要在项目设置里设置一下  设置为

![e415efaa-6fe9-43dc-851a-d0cb83492aac](./images/e415efaa-6fe9-43dc-851a-d0cb83492aac.png)



对于每一个网格我记得原理是会检测其和周围空间的边缘 在边缘的一圈应用这个材质。这里需要设置一下启动这个功能 以及自定义深度 

材质里设置了 250 深度为红色描边

![570d77ef-2587-4648-ad28-cc61b1e7563f](./images/570d77ef-2587-4648-ad28-cc61b1e7563f.png)



在材质的最前面有一个设置线条粗细的参数

可以调整 先设置1.6就好

![408d887f-7687-4375-8da6-0750d51c5632](./images/408d887f-7687-4375-8da6-0750d51c5632.png)



### 挑战

在C++的接口函数实现里做出这两个效果   

![55428403-9962-4287-b8b4-c19a167bcf07](./images/55428403-9962-4287-b8b4-c19a167bcf07.png)



## 第二章结束

主要就是配置了一些基础的角色控制 高亮

## 新知识点小结

check（） CastChecked() 可以方便的判断指针是否合法 

需要注意的是在发布版本中check语句的断言功能会被直接忽略 但是castchecked这种除了check的cast语义还是会正常执行



# 第三章

## GAS系统组成

![b94fbc9f-59f0-4d05-9c41-a0f4ecab0c2e](./images/b94fbc9f-59f0-4d05-9c41-a0f4ecab0c2e.png)

ability system component   为角色激活 添加 能力

attribute set

ability

ability  task

gameplay effect

gameplay tag



## ability suystemcomponent 以及attribute对于player来说应该放在那里

考虑到pawn可能会被销毁以及切换的原因

在playerstate上设置component 和attribute是比较合理的做法

![9f749ba7-3f08-409b-9f48-d8fa2c88e2ad](./images/9f749ba7-3f08-409b-9f48-d8fa2c88e2ad.png)

在此项目中会这样做

![87d8d6a3-8ade-4244-9dbb-007cc155bbdf](./images/87d8d6a3-8ade-4244-9dbb-007cc155bbdf.png)

## 创建playerstate

首先设置 playersyaye  的网络更新频率

当服务器上的数据变化时 服务器会尝试同步客户端  这个同步的频率就是网络更新频率

![d50a33dd-749c-4ff2-9ead-32b8755eec23](./images/d50a33dd-749c-4ff2-9ead-32b8755eec23.png)

然后创建对应的蓝图 将其分配至gamemode上

## 创建component attribute

注意 成员变量类型是父类 但是实际上生成的时候使用的是 Aura类



实际上GAS系统是一个插件 所以需要启用一下

![67fc0cfc-5444-4801-8bc6-b210c4bbc0a4](./images/67fc0cfc-5444-4801-8bc6-b210c4bbc0a4.png)

然后还需要加一下模块依赖

注意这里写法是有问题的 因为是直接继承了这些类 所以需要public添加依赖

![1473bb05-d64e-4375-a3c4-83e240568e91](./images/1473bb05-d64e-4375-a3c4-83e240568e91.png)



以及创建自己的com 和attri到 abilitySsystem目录 良好的资产管理也是需要注意的内容

### public依赖和private依赖有什么区别

```
Public = 我的头文件用到了，下游也需要知道；Private = 只有我的实现文件用到，外部不需要知道。
其实和是否可以提前声明类似  如果你在头文件里需要知道具体的类实现那么就需要publi依赖
```

## 多人游戏和GAS的关系

这里就可以很清晰的看到服务器和客户都安分别都存在些什么

![96882a2b-e7df-422c-8a8a-3966766ee308](./images/96882a2b-e7df-422c-8a8a-3966766ee308.png)

## 在character 基类中设置访问Gas内容指针

在enmycharacter初始化组件 和对象

在playerstate  也是一样 

并且实现gas的获取compoknent的接口   base character 和 playerstate都需要

自己可以单独实现一个获取aatribute的函数 接口就不必了

接口名如下

```
public IAbilitySystemInterface
```



![9daf3695-4db8-485f-8954-157fb3853a13](./images/9daf3695-4db8-485f-8954-157fb3853a13.png)



## 设置ASC复制模式

注意这里有一个内容是mixed

这里的注释是这样的

![18e22ddb14d74848b3f7229856354b26](/E:\UE5\NOTE\Aura/images/18e22ddb-14d7-4848-b3f7-229856354b26.png)

这是ge-- 影响游戏数值的效果如何在网络中复制的部分

我们在什么情况下应该选择什么模式呢

中间那列就基本标注了使用场景 单人游戏full 多人游戏player mixed 多人游戏ai minimal

![4c650cdb-4962-43f9-91a5-3408ea3c6a59](./images/4c650cdb-4962-43f9-91a5-3408ea3c6a59.png)





## 设置ASC Actor info

![c126e73e-70e2-4e28-b497-36e12b395354](./images/c126e73e-70e2-4e28-b497-36e12b395354.png)

![1165a020-f02a-45fe-a4bb-3791d7c88005](./images/1165a020-f02a-45fe-a4bb-3791d7c88005.png)



在多人游戏中对于设置AAI的实际就显得很重要

详见结尾知识补充



我觉得对于第一种的话其实直接都用client 的ackowledge不就好了  

对于AI来说只会在服务器存在 所以直接beginplay就好了

![ef35deaa-aa84-4fbd-92ef-00d6d4ec1e74](./images/ef35deaa-aa84-4fbd-92ef-00d6d4ec1e74.png)

### 挑战

![7dbf7f31-a213-4abf-9dd1-2770aee5b4ad](./images/7dbf7f31-a213-4abf-9dd1-2770aee5b4ad.png)







注意这里的代码是有问题的。在possessedby的时候只能说明pawn被controller控制了。这时候controller是有playerstate  的但是还没有设置给pawn 所以应该直接从controller获取playerstate而不是从pawn

但是我看教程里就是直接从pawn获取的就有点迷惑



喔喔看了一下，写道base去了神了。就写到polayercharacter就好 其实是两种都可以的

![e4720f7f-4fb1-4447-9568-c487f4542a5c](./images/e4720f7f-4fb1-4447-9568-c487f4542a5c.png)

![576fefde-7b92-42ad-9009-32a14c41d54a](./images/576fefde-7b92-42ad-9009-32a14c41d54a.png)



![bbcd2a18-703f-4747-800c-2eae97fa1405](./images/bbcd2a18-703f-4747-800c-2eae97fa1405.png)



## mixed模式补充

![f7cf7aa5-bcd9-4209-a14b-da726f39c3f9](./images/f7cf7aa5-bcd9-4209-a14b-da726f39c3f9.png)

主要就是说ability actor info 中的owner ，这个actor的owner必须是controller 在mix模式下



## 第三章结束小结

主要是创建了两个组件 ASC 与attribute 分别给playerstate 和  enemy base 实例化了   并且给所有的charatcer和palyerstate都提供了获取接口

然后设置了 actor info  



# 第四章

## 属性集

一个ASC可以拥有多个不同类型的属性集

当然全部属性放到一起也没有问题。甚至可以全部类都用一个属性集。因为这个其实不占用多少内存



使用GE的一个好处就是有客户端预测，在很卡的情况下也可以立刻显示数值变化

![c5bc6a89-b1f4-45ff-9e4d-904c98889d81](./images/c5bc6a89-b1f4-45ff-9e4d-904c98889d81.png)

一个Attribute 是一个FGameplayAttributedata类型的数据，他们多个被attribute set管理 

![46e3c0da-b5dd-4f56-9bdc-6cab2566ad60](./images/46e3c0da-b5dd-4f56-9bdc-6cab2566ad60.png)



## 为属性集添加属性

![6bf47f93-1a2d-416e-8a36-df2f6bcd163c](./images/6bf47f93-1a2d-416e-8a36-df2f6bcd163c.png)

我们在收到onrep后首先是需要通知GAS

![d0661c43-77bd-45eb-acb5-eb6621e5a9ac](./images/d0661c43-77bd-45eb-acb5-eb6621e5a9ac.png)

然后设置可复制变量。让其不管是否数据一直都继续同步   

因为可能有些技能是设置触发的，而不是变化触发  比如说想对设置这个行为做出反应

![a0cb5f56-97dc-44e6-b588-c91c6f581866](./images/a0cb5f56-97dc-44e6-b588-c91c6f581866.png)





### 挑战

注意流程

1. 创建FGameplayAtttributedata 

2. 标识可复制 然后创建onrep函数

3. 实现onrep函数，函数内调用GameplayAttribute_REPNOTIFY 宏来进行客户端预测

4. 在getlifeTime函数里添加该属性为可复制

5. ```
   按照这个做一下宏 然后为每一个属性都加上对应的获取函数，为什么可以看下一小节
   
   #define ATTRIBUTE_ACCESSORS(ClassName, PropertyName) \
   
   * GAMEPLAYATTRIBUTE_PROPERTY_GETTER(ClassName, PropertyName) \
   * GAMEPLAYATTRIBUTE_VALUE_GETTER(PropertyName) \
   * GAMEPLAYATTRIBUTE_VALUE_SETTER(PropertyName) \
   * GAMEPLAYATTRIBUTE_VALUE_INITTER(PropertyName)
   ```
   
   
   
   

![d9642723-2fbc-4181-b5fc-2c06aad65302](./images/d9642723-2fbc-4181-b5fc-2c06aad65302.png)

## GAMEPLAYATTRIBUTE_REPNOTIFY 宏说明

这里说是用来帮助进行客户端预测的

问题是。这个是怎么帮助客户端进行预测的。



![4088a7eb-50aa-4a43-91d8-dcbef41ee1f1](./images/4088a7eb-50aa-4a43-91d8-dcbef41ee1f1.png)



这里就需要提到之前PPT上说的

base value 了   这个base可不是出生基础值  而是网络预测基础值，即服务器验证OK的基础值。



![469eaf50-3991-45b4-b09e-4f62d20a3fd4](./images/469eaf50-3991-45b4-b09e-4f62d20a3fd4.png)

流程大概是这样的 这里可能需要一点本地预测的知识才能看明白

比如说客户端做了一个数值操作 100->80 这时候他本地预测了 current value已经变为了80 然后像server发送请求 说我变为了 80 

此时如果服务器认为OK 那么在onrep收到的就是90 这个宏会去设置base为80



如果认为不对。服务器会将他认为正确的值返回比如说 90 那么此时这个宏也会将base设置为90  如果后续没有客户端预测那么current也会变为90 如果有后续预测那么会在修正后的base基础上进行预测



那么如果不写这个宏会怎么样。首先就是服务器永远无法纠正客户端预测错误的值。他只会在错误上越走越远

## attribute accessor

虽然我们知道都是使用GE来修改数据 但是我们有时候需要获取数据 

所以可以定义这样的宏 来方便我们获取数据 和attribute

注意gameplayAttribute是一个gameplayAttributeData里的属性   其好像是一个属性的标识来的  因为data直接比数据会不同 

所以需要一个唯一标识符 就是gameplayAttribute   可以通过GAS提供的宏来方便的拿到



需要注意一下init 和set 的区别    init把base 和current值都设置为了一致    而set值设置了base

![3add66f5-edf2-4215-868b-4f71dcf2fca6](./images/3add66f5-edf2-4215-868b-4f71dcf2fca6.png)



所以可以直接按照他的建议来生成一下宏 然后给每一个属性都加上

这些宏记得放到public去，因为宏是文本替换嘛。所以你如果放在private那么其他的类里是用不了的

![7a29100f-dbc6-46f5-bc95-cd75404b5093](./images/7a29100f-dbc6-46f5-bc95-cd75404b5093.png)



### 挑战

![bcc63430-44f2-4b08-8541-a3f22ff61974](./images/bcc63430-44f2-4b08-8541-a3f22ff61974.png)

## 知识补充里有补充outer以及attributeSet是如何找到或者被ASC找到的

## 添加能直接修改attribute的actor  不久之后会换成ge

创建一个有sphereComponent static mesh 的actor

然后设置其on / end overlap委托回调 



这里使用const_cast来吧一个const对象转化成了可编辑对象。这可不行学，作为了解

![e5af6012-dc3b-4e08-8d5d-73f806efc98d](./images/e5af6012-dc3b-4e08-8d5d-73f806efc98d.png)



可以看到底层源码其实就是在一个个轮询ASC所管理的attributes 来看其是不是给定的那个UClass的子类

![3800ccfc-3b84-49f8-bb3a-34f5f06f554c](./images/3800ccfc-3b84-49f8-bb3a-34f5f06f554c.png)

如果是的话就返回



### 挑战

![eec583c3-f418-4465-9d01-6ee2ff734591](./images/eec583c3-f418-4465-9d01-6ee2ff734591.png)





## 第四章小结

1. 了解了添加attribute的5个步骤

2. 学习了是如何使用GameplayAttribute_REPNOTIFY来实现客户端本地预测的

3. 学习了ue中ASC是如何获取其管理的atrributeSet 的

4. 学习了UE的反射机制 uclass  当然只是皮毛
   
   
   
   
   
   

# 第五章

## UI架构

该如何以可拓展的方式来实现UI系统

其实主要就是实现VCM架构   我看弹幕说MVVM架构更适合游戏UI  后续可以看一下   我看说lyra就是使用的mvvm架构 后续可以一起看了

VIEW只负责展示相关逻辑   controller负责从model获取数据并进行初步加工   model负责存储基础数据

![ceade29a-7ab4-4c9f-9d4d-dde7fa857236](./images/ceade29a-7ab4-4c9f-9d4d-dde7fa857236.png)

就是做这种单向依赖 就替换下层 上层是没有感知的

![62980358-628a-4bc3-9475-dfe18e526488](./images/62980358-628a-4bc3-9475-dfe18e526488.png)





![92d7ebad-1f96-4aac-92a8-f55abe43005b](./images/92d7ebad-1f96-4aac-92a8-f55abe43005b.png)



## 创建需要的子类

### uuserwidget子类  作为view

记得加一下UMG模块

![3a68c408-831e-483f-801c-6d9681ac46c5](./images/3a68c408-831e-483f-801c-6d9681ac46c5.png)

然后在调用setcontroller的时候调用WidgetsET来初始化 这个依赖是单向的，controller并不知道有哪些widget依赖于他



### uobject子类作为controller

对于controller需要去访问data base 

我们的项目中data base就是 player state   player controller   ASC   Attribute

这几个，所以对于controller来说这些都应要获取到

![35c14418-ba5f-4920-b9d8-9464f23a1a63](./images/35c14418-ba5f-4920-b9d8-9464f23a1a63.png)



## 根据view创建一个widget蓝图来做血条

因为血条会和蓝条类似  所以做一个基类 大家都可以继承于这个

如果想要能够重写size

那么就拖一个sizebox 然后修改填充规则为desier 然后重置该大小

![bae95fe5-809e-4b6f-9f0c-17cf17227bd5](./images/bae95fe5-809e-4b6f-9f0c-17cf17227bd5.png)



然后如果想要继承的话 需要勾选提升为变量选项 就可以在事件图表中找到这个变量了

![4d92e070-a909-4fb0-ba75-67c8c7b13bb8](./images/4d92e070-a909-4fb0-ba75-67c8c7b13bb8.png)



然后可以自己建俩变量，在preconstruct里设置box大小

![58d4da05-5f99-4ff1-92c9-21a55b656bce](./images/58d4da05-5f99-4ff1-92c9-21a55b656bce.png)

preconstruct节点就是只要蓝图中的属性变化了那么就会执行这个节点

然后添加一个overlay   一个让UI可以队堆叠的组件

然后拖入一张image作为背景图  然后选择为填充  其作为图片的brush我们需要自己创建一个变量 并且用其来设置笔刷

记得勾选image也为virable因为我们需要改变他

![6d07e9e2-2425-4e4f-ba86-48ff2d099f1b](./images/6d07e9e2-2425-4e4f-ba86-48ff2d099f1b.png)



然后属性很多的话可以在这里修改其category来分类

![be1e0ba5-5e19-4bc5-bebb-d9e12f430446](./images/be1e0ba5-5e19-4bc5-bebb-d9e12f430446.png)



然后进度条就是一个progressbar

需要设置其

![917bf91e-3361-4da3-8006-55058ff691f7](./images/917bf91e-3361-4da3-8006-55058ff691f7.png)

和

![f10904a5-31fd-4f3e-94ed-d222b65eef4c](./images/f10904a5-31fd-4f3e-94ed-d222b65eef4c.png)

这样他才会绘制为一个image

![3d105cdd-84b2-4e99-a827-1d2ae84ebe9e](./images/3d105cdd-84b2-4e99-a827-1d2ae84ebe9e.png)

然后把background的alpha设置为0把背景露出来

然后设置进度条的填充方式为由下到上

![18432138-36ee-4681-b203-e05dc5af5114](./images/18432138-36ee-4681-b203-e05dc5af5114.png)



当然这个进度条的图像也要设置为可修改

![739138b2-a0df-4903-b617-a7ff3ef28092](./images/739138b2-a0df-4903-b617-a7ff3ef28092.png)



然后也要可以设置padding 这样可以让图片往里缩

![1cd7d2b9-a75d-4d05-9ae4-5567611c8090](./images/1cd7d2b9-a75d-4d05-9ae4-5567611c8090.png)



然后还要加一个玻璃罩

以及设置其图片和poadiing

![cb1d3ed5-80d1-4d8b-8492-30994e6e7b6b](./images/cb1d3ed5-80d1-4d8b-8492-30994e6e7b6b.png)



## 根据基类创建血条UI

创建一个overlay来放置小组件 当然这个overlay也是aura widget

对于小组件用boxsize来确定大小和位置就好了说是因为canvas比较昂贵   但是对于overlay这个全局唯一的就无所谓了



快速验证的话可以在level蓝图里快速的验证

![e70507d7-cff9-45ea-91fd-8bf805c6af1e](./images/e70507d7-cff9-45ea-91fd-8bf805c6af1e.png)



注意左边的哪些创建出来的属性 把可见性打开就可以在每一个子类中修改

拖入overlap的时候记得勾选真实尺寸

![115d716d-938a-434c-a578-56ac6eaf9e88](./images/115d716d-938a-434c-a578-56ac6eaf9e88.png)





### 挑战

![91596b8d-48dd-4621-8e28-89b8be4149f1](./images/91596b8d-48dd-4621-8e28-89b8be4149f1.png)





## 重写HUD

![f08240e8-dcf9-4d6e-a471-c5db5cd97aa0](./images/f08240e8-dcf9-4d6e-a471-c5db5cd97aa0.png)

然后再gameplay里边创建widget并且添加到试图

但是后续controller分配的话  时机可能不太对



### 挑战

![44d5beca-aa4e-4a13-8b5a-8a6fdb91dd3a](./images/44d5beca-aa4e-4a13-8b5a-8a6fdb91dd3a.png)



## 初始化widget controller

自定义一个结构体包含需要传递的几个参数

![4acb3e8e-5cbd-49db-863a-20c042222341](./images/4acb3e8e-5cbd-49db-863a-20c042222341.png)



添加一个从结构体设置controller的函数



### 然后将其作为基类 派生出对应的widget所需要的contgroller

然后对于overlay的controller检查其是否存在  就相当于只获取一个单例的形式

![ab50b6f9-afd2-4b56-9f52-cd29a1e31456](./images/ab50b6f9-afd2-4b56-9f52-cd29a1e31456.png)



![14cf2f29-0e20-49eb-8df7-a8b58db91b7d](./images/14cf2f29-0e20-49eb-8df7-a8b58db91b7d.png)





### 挑战

想一下在哪里可以安全的调用initoverlay

监听服务器 直接在possessed就好 但是客户端应该不能再onrep_ps吧  那个时候pc又不一定好了

![f78745a6-0d6c-4efe-b0ad-cc4eb4537d5d](./images/f78745a6-0d6c-4efe-b0ad-cc4eb4537d5d.png)

这里其实就和init actor info一起就好了

在服务器上直接possesedby

在客户端上

onrep_ps的时候 ps asc as 都时就绪的 但是不一定可以从pawn获取到controller 因为onrep_ps heonre_pc没有一定的先后顺序  

但是controller在本地是连接的时候就初始化好了，只是没有分配pawn 所以其实可以从`GetWorld()->GetFirstPlayerController()`  来获取到本地controller

记得判断一下pawn是不是被本地操作的

![8fcf303a-002f-4e99-b429-ae4d5e1f6b97](./images/8fcf303a-002f-4e99-b429-ae4d5e1f6b97.png)





## 实现数据广播

其实就是依赖于委托  委托是很好的单向依赖方式 被注册的一方并不需要知道谁注册了。只需要在出发的时候把所有的回调都调用就好

### 代码规范

声明委托类型时加上signature可以方便的看出来这是一个委托类型而不是对象

![3b56196b-8068-4b8c-b6a7-949eab898a2f](./images/3b56196b-8068-4b8c-b6a7-949eab898a2f.png)

### 挑战

通过controller 的as获取真正的当前生命值将其广播出去

![50530c06-bcb0-4ab0-b39b-2a5135ad91f8](./images/50530c06-bcb0-4ab0-b39b-2a5135ad91f8.png)

### 然后因为我们设置的时overlay的widget的controller

但是其实两个 progressbar是 没有controller的

这一部分就可以交由蓝图实现函数自己处理了 就不用再C++里面搞

记得把成员wiget提升为变量



![4da14910-463c-477c-874c-30c6e35a3902](./images/4da14910-463c-477c-874c-30c6e35a3902.png)

然后会往下触发血条的onset  这时候其实就可以转化controller为具体的controller然后订阅委托绑定自己的函数

这里就全部是蓝图在做，主要是如果C++做的话。每一个都会有自己的类和重写函数 有点麻烦 ，而且有类之后还要创建蓝图多此一举



同时如果要在蓝图里可以转换这个类型的话类需要标记为可转化蓝图和可生成蓝图   然后那两位委托也要设置蓝图可绑定

![f3a20d79-32f4-44f9-94e2-68685600a419](./images/f3a20d79-32f4-44f9-94e2-68685600a419.png)

![879777ad-aae5-49cc-9080-fc88e0a2b827](./images/879777ad-aae5-49cc-9080-fc88e0a2b827.png)

再绑定的时候蓝图自己会生成一个对应的事件

![9d7b2037-03d6-4e18-9256-e7943b20b3c8](./images/9d7b2037-03d6-4e18-9256-e7943b20b3c8.png)



但是有个问题说是蓝图没法设置父类的组件 这么蠢啊  

但是实际上我看子类可以直接设置啊



这里理解不太对详见知识补充 

## widget controller 监听AS变化

![ad6dd453-bb3e-4b3b-8df9-7cb78028ae0e](./images/ad6dd453-bb3e-4b3b-8df9-7cb78028ae0e.png)

这是一个多播委托意味着其是没法在蓝图绑定的 而且需要用addUObject



然后所有的widgetcontroller都应该绑定其管理的属性。所以做到base里去

![ea332310-9c16-490c-9ec1-6a058cbd36bd](./images/ea332310-9c16-490c-9ec1-6a058cbd36bd.png)



然后回调签名是这样的 当然可以去委托类型那里看

![26f6845a-fa9a-4aa7-8756-c0f8cc5b1c8e](./images/26f6845a-fa9a-4aa7-8756-c0f8cc5b1c8e.png)

然后变化的回调里就可以直接通过data.NewValue获取数据

![520e7805-375f-4386-babd-4943423fb463](./images/520e7805-375f-4386-babd-4943423fb463.png)



### 挑战

![74f520b9-b046-4383-bb2d-440d13d821ae](./images/74f520b9-b046-4383-bb2d-440d13d821ae.png)

## 挑战

设置mana的一系列回调

## 第五章小结

很好的一章。搭建了一个完整的mvc架构。model提供属性变化的委托  对于绑定到其委托上的controller并不在意

controller 在绑定model委托的同时 为view提供委托 表明数据变化以及提供变换后的数据   controller层后续可能会在绑定到model的回调里有更多复杂的处理 目前只是透传   。

view层就只关注与自己的逻辑 如何更新UI





对于更多新的UI的话，比如说个人属性？就创建一个新的widget和新的controller就好  就这条链路是不会变的



## 第六章

![05f64271-078f-427d-a359-14f6ec2cf97e](./images/05f64271-078f-427d-a359-14f6ec2cf97e.png)

![3c21b3a3-5acb-4769-b69f-05a69ec3fcea](./images/3c21b3a3-5acb-4769-b69f-05a69ec3fcea.png)



## 修改Actor类 比如说那个药瓶

其网格和碰撞体形状应该由蓝图的设计师来完成

C++应该只负责其碰撞逻辑就好了

并且修改之前的硬编码修改as 改为使用ge来修正



使用GAS静态库 来获取ASC对象

![1926a055-8e96-4404-a346-955bf8f6cbc3](./images/1926a055-8e96-4404-a346-955bf8f6cbc3.png)

ASC只要有Ga的uclass指针就能做出对应的spec来

然后还需要一个context指针

但是我们通过会获取一个handle 其实就是一个包装器 ，其内部的成员变量DATA  就是实际的context指针    包装器内为我们包装了很多有用的函数

![761315fd-b796-45d2-921c-9c3fbc48335f](./images/761315fd-b796-45d2-921c-9c3fbc48335f.png)

比如说添加造成者。可以看到他也是直接将造成者放入了Data即context的成员里

![ef0a69e9-ac7f-4f02-99a3-74f907e4af0b](./images/ef0a69e9-ac7f-4f02-99a3-74f907e4af0b.png)

所以可以简单这样理解。ge只是单纯的造成效果而已。而context是其造成效果的背景



然后ge spec 其在outgong spec时的返回值时一个spec handle也是一个包装器

![84cb7a2e-baa0-4f76-83fa-4682752f9829](./images/84cb7a2e-baa0-4f76-83fa-4682752f9829.png)



### context

可以看到ASC的makecontext函数内部

其实就是用一个创建的context初始化了handle 

然后设置了context

![ef0234d1-fdc6-4df4-83e3-98ad697c81e0](./images/ef0234d1-fdc6-4df4-83e3-98ad697c81e0.png)

然后使用包装器函数往里边设置了instigator 和 causer作为默认的造成者。当然对于我们这里是不合理的因为这个其实是受害者的ASC

![694c7dca-0996-42e1-86a7-0d714c20088d](./images/694c7dca-0996-42e1-86a7-0d714c20088d.png)

### effect spec

可以看到就是把传入的等级 uclass创建的实例  和context传入来构造了specc   然后用spec入参构造了 spechandle  

![d020cb76-9564-4b09-a85e-030a91f78c7d](./images/d020cb76-9564-4b09-a85e-030a91f78c7d.png)

### 然后applyEffect就只要一个effectSpec就好 里面已经包含了所有的需要信息

![2cacff69-1478-4b2e-99f1-20b0db85bf85](./images/2cacff69-1478-4b2e-99f1-20b0db85bf85.png)



### 当然记得设一下Source

这些context都是随便使用者设置的 只要能够分清楚用途就好

![20323257-0419-4cd0-b15b-093ffdef52be](./images/20323257-0419-4cd0-b15b-093ffdef52be.png)



## 创建instant GE

因为GE其实很完善了， 所以不需要重写C++类

对于某个特定的道具的GE  看你怎么安排文件归类把

都可以



### 挑战

![7d91f01e-734f-4cc5-afea-d49585a065cd](./images/7d91f01e-734f-4cc5-afea-d49585a065cd.png)

## 创建duration GE

在C++里加一个持续时间GE class变量

注意如果对一个duration GE设置持续时间 但是不设置周期 他的逻辑其实就是临时获取该数值   

只有设置了周期才是会一段时间跳一次



![69911eb6-0d89-44ba-8d26-8a3856098755](./images/69911eb6-0d89-44ba-8d26-8a3856098755.png)

### 挑战

![278050b7-5e5b-4f9c-8345-36f7a6cef15e](./images/278050b7-5e5b-4f9c-8345-36f7a6cef15e.png)





## 创建periodical GE

其实就是在duration的基础上加一下触发周期就好

![8af31c64-4b40-4dbc-bd87-c8eda504c456](./images/8af31c64-4b40-4dbc-bd87-c8eda504c456.png)

这个勾选框指的是是否在GE应用的第一时间就触发一次周期GE，不勾选的话就要先等一个周期再触发

![4e7a0c68-0f62-488d-a744-8fb449f6cb61](./images/4e7a0c68-0f62-488d-a744-8fb449f6cb61.png)

怎么5.8没有这个被阻塞策略了

![8b50af22-796c-4e99-89fe-736cf9795642](./images/8b50af22-796c-4e99-89fe-736cf9795642.png)

需要设置周期不为0才有

![171b3cc6-fff4-4a55-b75c-10febbe88f9b](./images/171b3cc6-fff4-4a55-b75c-10febbe88f9b.png)

### stack策略 堆叠策略

就是有多个非instant 的ge应用于一个ASC时应该如何操作

### 挑战

创建一个周期性恢复mana的actor

![4ffdd184-c99f-4414-b1cf-9bc0dd27b2d9](./images/4ffdd184-c99f-4414-b1cf-9bc0dd27b2d9.png)





## 效果堆叠

有三种  不堆叠  按照来源堆叠   按照目标堆叠

![fab4693e-955a-4a19-b300-4e0e284a9bba](./images/fab4693e-955a-4a19-b300-4e0e284a9bba.png)



如果设置不堆叠的话 他其实就是相当于执行了三次GE 他们会分别走完自己的周期 即如果一个GE恢复10点 那么 3个恢复30点 



然后设置堆叠的话其实还是有多少层就会叠加多少次应用 比如有3层那么还是一秒恢复30点

但是持续时间就是由设置的堆叠策略来定了。就不是每个GE单独计算自己的时间，而是一个计时器，不过层数为3，但是应用数值还是照样堆叠



```
你的理解非常准确。这正是 GAS 处理“多实例”与“单实例堆叠”的核心区别。为了让你彻底理清逻辑，我们可以把这两种情况拆解对比：

情况 A：不开启堆叠（独立实例）
如果你对目标施加了 3 次同一个 GE，且该 GE 没有开启 Stacking：

实例数量：目标身上会有 3 个独立 的 GE 实例。
数值计算：每个实例都会运行自己的周期计时器（Period Timer）。在每一秒结束时，3 个实例分别触发一次 -5 的效果。总表现为一秒内扣了 5 + 5 + 5 = 15 滴血。
时间计算：完全独立。
实例 1 在第 1 秒施加，第 5 秒结束。
实例 2 在第 2 秒施加，第 6 秒结束。
它们互不影响，各自到期后自我消除（Eliminate）。
情况 B：开启堆叠（单实例计数）
如果你开启了 Stacking（以 Aggregate by Target 为例）：

实例数量：目标身上只会存在 1 个 该 GE 的实例，但它的 StackCount（层数）变量变为了 3。
数值计算：系统只有一个计时器在跑。每隔一秒，系统查看当前层数（3），执行逻辑为：单层数值(-5) * 层数(3) = -15。
时间计算：由堆叠政策统一管理。此时你看到的 Stacking 设置项就开始起作用了：
1. 持续时间如何依托设置？
在堆叠设置里，你可以决定新的一层进来时，这“一个实例”的寿命怎么算：

Refresh Duration（刷新持续时间）：只要新加一层，整个 GE 的剩余时间重置为最大值（比如总长 5 秒，在第 4 秒加了一层，它又变回 5 秒）。
Never Refresh（从不刷新）：第一个 GE 什么时候过期，整个堆叠就什么时候一起消失，不管中途加了多少层。
2. 周期计时器（Period）的特殊处理
这里有一个容易被忽略的设置：Stack Period Reset Policy（堆叠周期重置政策）。

Reset Period on Stacking（堆叠时重置周期）：每当加一层堆叠，每秒扣血的那个“1秒闹钟”就重新开始计时。
风险：如果玩家手速极快，在 0.9 秒时加了一层，闹钟重置，可能导致这 15 滴血迟迟扣不出来（因为始终跑不满 1 秒）。
Never Reset（从不重置）：闹钟照常跑。不管你中间怎么加层数，每到整秒就按当时的层数扣血。这是最常用的设置。
总结对比表
特性    不堆叠 (3个GE)    开启堆叠 (3层)
计时器    3 个闹钟独立跑    1 个闹钟跑
数值    3 次独立的 -5    1 次合并的 -15
到期消除    各过各的，分批消失    根据政策，要么一起消失，要么层数逐层递减
性能    较高（实例多）    较低（节省资源）
结论：你的理解是正确的。开启堆叠后，数值确实是 层数 * 基础值，而时间的生命周期则完全交由 GE 蓝图中的 Stacking 策略 来定义。如果你希望模拟那种“每个 GE 独立计算时间，但数值叠加”的效果，通常会使用 Stack Expiration Policy 设置为 Remove Single Stack（到期只减一层，而不是全部消除）。
```





### 按照来源堆叠



注意这里的来源指的ASC是 因为我们其实是用自己的ASC来执行的satack所以 这两种情况都只会堆叠2次

![9164ec6a-fddd-414b-8825-70684899e306](./images/9164ec6a-fddd-414b-8825-70684899e306.png)



### 按照目标堆叠

![3c0686c1-b92e-4011-a1d6-4fba46f0115c](./images/3c0686c1-b92e-4011-a1d6-4fba46f0115c.png)

### 周期，持续时间 ，层数选项

选项分别为 刷新持续时长

不刷新时长

增加时长

![6aa3bb3b-f748-4d1b-8d60-19a303d9667a](./images/6aa3bb3b-f748-4d1b-8d60-19a303d9667a.png)



选项分别为直接执行下一次周期并按照该周期之后运行  

不跳过本次周期

![7c4d0300-a8d6-4d00-897b-e11fe4f5d2ec](./images/7c4d0300-a8d6-4d00-897b-e11fe4f5d2ec.png)



分别为直接清楚所有stack

减少一个stack并重置周期

单纯重置周期，这会导致GE效果为无限。但是是有地方手动减少计数的

![ed0189be-2da9-4247-9fcd-3ef580c49901](./images/ed0189be-2da9-4247-9fcd-3ef580c49901.png)





## infinite GE

同样的在C++添加一个Inifnite ge

就是把持续改成无限就好



然后我们想更灵活的配置GE的应用和取消的话

他是在C++里加了几个枚举来做



这是在干嘛，一个ACTOR会应用多个GE嘛，为什么搞这么多   

主要是看下应该怎么取消一个GE





可以看到激活其实是有句柄返回的

![56cdee3c-b32a-45b3-a515-b785b7564fad](./images/56cdee3c-b32a-45b3-a515-b785b7564fad.png)



其实就是需要将actor 和其附加的无限GE的句柄绑定到一起

可以写两个函数来做，但是我们也可以判断uclass的时间政策是怎样的

时间政策在GE里需要解开handle 解开spec去找

![94824cf5-3e13-43ed-a386-1ba2c4ddae26](./images/94824cf5-3e13-43ed-a386-1ba2c4ddae26.png)

其实就是一句话可以说好的类。就是需要存下ActiveGEhandle 和其对应的Actor

![8243695f-cb06-48fd-92db-850d17028686](./images/8243695f-cb06-48fd-92db-850d17028686.png)



既然他认为可能会触发多个GE，那完全就没必要这么写。。我后面自己重构下把

感觉可以自己搞个结构体 做成蓝图可见 然后直接做一个GE数组

以及第二个参数其实是，一次一处多少stack，因为如果开启堆叠的话就只有一个GE句柄，不过层数堆叠而已。不写的话默认是-1 就是移除所有

![1cdc1780-1e20-4f8e-a5b7-9ffa004a1158](./images/1cdc1780-1e20-4f8e-a5b7-9ffa004a1158.png)

## 挑战

我本来还在想呢

![b0a93e43-dfa0-4a8a-bd7b-028e318444d8](./images/b0a93e43-dfa0-4a8a-bd7b-028e318444d8.png)





优化了一下舒服多了

## 设置属性值上下限

这是AS的一个虚函数 每一个属性被修改的时候都要走这个

只建议在这里边做clamp

![d3a72f89-a653-4d3d-a325-f1f76ffee4f6](./images/d3a72f89-a653-4d3d-a325-f1f76ffee4f6.png)



![492f2403-b47b-4463-a1ed-1101206eb7e5](./images/492f2403-b47b-4463-a1ed-1101206eb7e5.png)



说这个并不是最好的处理方法，下一章会讲最好的。我这里就没有写了



## postGameplayEffectExcute

![0c33e1ac-1194-4e47-858e-c16369bf2bc8](./images/0c33e1ac-1194-4e47-858e-c16369bf2bc8.png)



在这个Data里面有很多参数可以获取  effectSpec   Target   以及evaluateData那里面有attrute 和变化的幅度



几乎是所有的GE执行的内容 所以是很重要的

![be48923d-1d38-444e-aec4-5d08b5483ac3](./images/be48923d-1d38-444e-aec4-5d08b5483ac3.png)



他这里好像在提前获取很多数据啊 。应该是为了之后做伤害逻辑用的。但是我觉得有点奇怪的就是之前我们的药水和环境伤害什么的是调用的AUra的Asc来应用的伤害啊。这个不就是我杀了我自己吗

![ba8f0067-01ec-46b2-8b09-616c7c01f1a4](./images/ba8f0067-01ec-46b2-8b09-616c7c01f1a4.png)



### 挑战



![f883f556-d627-43f2-b2a7-726175d45695](./images/f883f556-d627-43f2-b2a7-726175d45695.png)



主要是context里面有很多东西 可以看一下

源码里是这么写的  感觉是要啥再拿啥  和ASC相关的东西都能拿出来  



```
static UE_API bool CanActorReferenceBeReplicated(const AActor* Actor);

    // The object pointers here have to be weak because contexts aren't necessarily tracked by GC in all cases

    /** Instigator actor, the actor that owns the ability system component */
    UPROPERTY()
    TWeakObjectPtr<AActor> Instigator;

    /** The physical actor that actually did the damage, can be a weapon or projectile */
    UPROPERTY()
    TWeakObjectPtr<AActor> EffectCauser;

    /** The ability CDO that is responsible for this effect context (replicated) */
    UPROPERTY()
    TWeakObjectPtr<UGameplayAbility> AbilityCDO;

    /** The ability instance that is responsible for this effect context (NOT replicated) */
    UPROPERTY(NotReplicated)
    TWeakObjectPtr<UGameplayAbility> AbilityInstanceNotReplicated;

    /** The level this was executed at */
    UPROPERTY()
    int32 AbilityLevel;

    /** Object this effect was created from, can be an actor or static object. Useful to bind an effect to a gameplay object */
    UPROPERTY()
    TWeakObjectPtr<UObject> SourceObject;

    /** The ability system component that's bound to instigator */
    UPROPERTY(NotReplicated)
    TWeakObjectPtr<UAbilitySystemComponent> InstigatorAbilitySystemComponent;

    /** Actors referenced by this context */
    UPROPERTY()
    TArray<TWeakObjectPtr<AActor>> Actors;

    /** Trace information - may be nullptr in many cases */
    TSharedPtr<FHitResult>    HitResult;

    /** Stored origin, may be invalid if bHasWorldOrigin is false */
    UPROPERTY()
    FVector    WorldOrigin;

    UPROPERTY()
    uint8 bHasWorldOrigin:1;

    /** True if the SourceObject can be replicated. This bool is not replicated itself. */
    UPROPERTY(NotReplicated)
    uint8 bReplicateSourceObject:1;

    /** True if the Instigator can be replicated. This bool is not replicated itself. */
    UPROPERTY(NotReplicated)    
    uint8 bReplicateInstigator:1;

    /** True if the Instigator can be replicated. This bool is not replicated itself. */
    UPROPERTY(NotReplicated)    
    uint8 bReplicateEffectCauser:1;
```



自己的代码实现如下

先拿俩ASC其他的都可以衍生出来 

![9c42c3e6-7492-4eb0-aacb-bdac4dd8126c](./images/9c42c3e6-7492-4eb0-aacb-bdac4dd8126c.png)



## 使用curve Table

curve让我们可以根据一个等级曲线来实现自己的效果

一个是曲线 一个是表格  按这个三角可以加一列表格   然后在曲线视图就可以直接看到用加点方式做的曲线

![6f9b92da-67e1-415c-a356-421d9bbcf606](./images/6f9b92da-67e1-415c-a356-421d9bbcf606.png)

![a5edeba3-f06c-40ac-a6c3-0447b13a876c](./images/a5edeba3-f06c-40ac-a6c3-0447b13a876c.png)

需要设置一下系数  表格 和需要选择的曲线

![f1d54d66-38d0-4bcd-ac4f-b68be0ecadf6](./images/f1d54d66-38d0-4bcd-ac4f-b68be0ecadf6.png)



然后做effect spec的时候不是要传入context + level嘛  这个就会根据那个level来算出来具体的结果值

当然这个level有多种方法可以去设置。比如说根据角色的等级 ...

但是他这里是直接给item加上了level



因为一张表可以有多个曲线。所以其实理论上来说所有的曲线数值都能一张表做完



### 挑战

![f2787f0f-b119-448a-aa9d-50c2ad923ab5](./images/f2787f0f-b119-448a-aa9d-50c2ad923ab5.png)





## 第六章小结

这一章主要是学些了GE 了解如何从ASC中创建context 然后通过outgongSpec传入Uclasss gelevel context 获取spec然后应用ge 可以获取activateGEhandle 

该handle可以removeGE 



然后讲解了各种持续时间的GE  以及GE的堆叠效果  指的注意的是  堆叠是数值也是会跟随层数叠加的，并不是堆叠了就只生效一层数值。然后其持续时间就看堆叠那块怎么设置的



以及preChange里clamp数值上下限。但我看他那意思好像要在post里改吗

PostGEexecution  只要是通过GE数值变动 每一个都会走到这类来。其传入的DATA里有此次执行的全部所需数据。要啥拿啥



# 第七章  gameplay tag GT

## 概念

![176f3b17-d8bb-4372-a121-201552879338](./images/176f3b17-d8bb-4372-a121-201552879338.png)



GT 真的用处很多 可以用来做前置条件  和 各种组织条件

![d1518be3-be2e-42bd-8c26-4a47920af356](./images/d1518be3-be2e-42bd-8c26-4a47920af356.png)



## 在EDITOR创建GT

在项目设置里就可以添加

![54242dd1-b9dd-479d-a079-b6c61a9eb519](./images/54242dd1-b9dd-479d-a079-b6c61a9eb519.png)

他创建了一个属性的标签   不是很清楚AS的标签有啥用 先创建把   然后其配置文件就是在config 文件夹里 

![fdcb52b7-d49a-4829-94c2-dd8772bde2bb](./images/fdcb52b7-d49a-4829-94c2-dd8772bde2bb.png)



## 使用数据表添加GT

这种方法要好一点。因为可以随时进入那个表很方便的改

![68b75a1d-643b-48ea-9730-5a14a1d06e35](./images/68b75a1d-643b-48ea-9730-5a14a1d06e35.png)

![f53d69ed-491c-46d9-b4c3-b41b531843f5](./images/f53d69ed-491c-46d9-b4c3-b41b531843f5.png)

然后就可以在这里编辑



![de11fd5e-27e0-4b7b-adf3-44cc111b2e61](./images/de11fd5e-27e0-4b7b-adf3-44cc111b2e61.png)



但是这回还不会生成GT 需要到项目设置里加入数组才行

![3bcad868-ca2c-4f2c-bffa-1664085b14e9](./images/3bcad868-ca2c-4f2c-bffa-1664085b14e9.png)







## 如何把GT加入ASC

### 使用GE

GE的tag 部分有很多 一个个来看一下

#### GE自身持有的GT

这个是GE本身自带的GT 其不会赋值给ASC    但是我看5.8好像都没有这个Tag页了     先看看视频的吧 。肯定是被放到其他的UI里去了

然后这里分别指的就是combine tags即从GE父类继承来的tag   added 自己希望额外加入的tag   removed 希望移除父类的tag

但是因为我们一般不会继承GE  所以这个没啥实际用处 了解就好

![73e195d4-f7d0-4e46-966a-fa4ed29c4e74](./images/73e195d4-f7d0-4e46-966a-fa4ed29c4e74.png)

5.8是在这里

![1670ba00-b4bd-4287-9b39-56c53402077f](./images/1670ba00-b4bd-4287-9b39-56c53402077f.png)

 

#### GE应用GT给ASC

如何设置就会给ASC添加标签   注意 只有有持续时间的GE才能添加GT 因为在GE结束时 其GT也会一起被删除

喔喔 他上面那个combine tags就是整合了 父类 ，然后自己的add 和remove 就是一个集成的作用 就是编译了之后在combine里面就是所有的效果

然后在showdebug里面是可以看到tags的  还可以看到层级

但是这里就算捡起来了多个GE 效果ACTOR还是只有一层tag  因为我们如果设置了堆叠·的话其实 他指的是游戏效果的可堆叠   

但是如果设置GE为不可堆叠，那么他们本身都是单独的GE 就会有多层tag 

![1234fb0c-06b7-4197-8dc7-1d452d1519dc](./images/1234fb0c-06b7-4197-8dc7-1d452d1519dc.png)

![a9c8957b-0e57-4031-8387-572b9d646a05](./images/a9c8957b-0e57-4031-8387-572b9d646a05.png)

在ASC源码里有这些委托  有空的话可以看ASC的源文件

![54d92957-779e-47af-8da7-ac74eced6cba](./images/54d92957-779e-47af-8da7-ac74eced6cba.png)



这甚至还有移除时的委托

![b14a5785-2a11-4102-b04e-db62a38a0d4e](./images/b14a5785-2a11-4102-b04e-db62a38a0d4e.png)



## 绑定GE应用时回调

来看看执行了哪些GE

![2bcffab8-3a60-463c-b032-4f9dd3286719](./images/2bcffab8-3a60-463c-b032-4f9dd3286719.png)

这个第三个参数其实是apply时返回的那个句柄 可以用来取消效果来着

直接写道ASC里面就可以

然后触发时机还是和之前的init actor info一致



介于enemy可能也会需要绑定一些委托 但是大家的不一样。所以可以在基类里写一个虚函数



## 他想在HUD上以TAG来显示这些被施加了某种GE

首先gespec是可以看到自己的Asset TAG的 

他是从ASC里注册了第一层委托。然后自己建一个委托来广播所有遍历到的tag 

然后widget controller里会绑定自己的回调去处理每一个tag   

我其实在想为什么不直接用widget controller去绑定ASC的GE执行回调。  一个可能的解释是ASC里边还想处理些其他功能吧



![ffc355ad-ae7b-47dd-af57-aec0122a7a72](./images/ffc355ad-ae7b-47dd-af57-aec0122a7a72.png)



在widget controller里面注册了回调  使用的lamda 可以是可以 但是lamda匿名的话 很容易找不到数据流向我个人是不太喜欢

![64e48db5-438c-4256-bf09-7999a6be0b39](./images/64e48db5-438c-4256-bf09-7999a6be0b39.png)



### 定义data table来 自定义表结构

用来显示怎么样的tag 需要显示什么样的数据

![e3b07207-80e8-42c7-b2f5-b2f716db4963](./images/e3b07207-80e8-42c7-b2f5-b2f716db4963.png)



然后就可以自建数据表了



然后对应的道具也需要对应的tag 可以自己重新建一个可拾取道具的表

然后他给加到成员变量里面 。。我说实话真神了，怎么都是倒着讲的，如果不知道全流程根本都不知道他一步步的意义是什么

![4767125a-750f-463a-b2c4-f86fb6299f7b](./images/4767125a-750f-463a-b2c4-f86fb6299f7b.png)



### 创建好之后，说是会根据tagname去查table的条例name

所以 rowname 得和tagname一致

![fa5a77fa-4b0c-400d-9428-1f1b1f267aef](./images/fa5a77fa-4b0c-400d-9428-1f1b1f267aef.png)



然后记得得给ge加上对应的标签

然后他做了一个模板函数用来返回指定的row类型的行 然后通过tagname查找

![241a5526-ceb3-467b-9d4e-76ac2cc76fc2](./images/241a5526-ceb3-467b-9d4e-76ac2cc76fc2.png)



### 创建view使用的委托

在此之前，在从maessage table中找tag之前可以判断一下找的tag是不是message来优化一下性能



![fa3587a6-8bb0-45c6-ab9c-a80c984e03a6](./images/fa3587a6-8bb0-45c6-ab9c-a80c984e03a6.png)



### 挑战

![f8788882-481a-47b0-9ca1-1251ef58c534](./images/f8788882-481a-47b0-9ca1-1251ef58c534.png)



## 创建显示消息的widget组件

UI布局大概是这样的  一个纵向布局  把text和image提升为变量了

他是直接在overlay上创建了widget 。我可能会在某个地方再加一个专门用来放消息的widget  然后生成和消失吧。先把他要做的看完。我再自行发挥

![d791615d-cc8e-4b39-9c67-4ea9f90b6158](./images/d791615d-cc8e-4b39-9c67-4ea9f90b6158.png)

![391b4318-8b46-409e-921d-455fb6b41ead](./images/391b4318-8b46-409e-921d-455fb6b41ead.png)



然后消失效果是做的widget animatiron来播放  

我可能继承一个C++类来处理生成的组件移动 蓝图里做有点大分

移动我自己处理。然后透明度倒是可以用动画来做



## 挑战

将widget controller中间广播数据变化的function改成lamda

![25730869-2ffc-4986-b26b-29bb7624e587](./images/25730869-2ffc-4986-b26b-29bb7624e587.png)



然后还修改了一下委托的类型。因为其实委托类型都是一模一样的，只是我们创建的变量不同而已

![a6db7ad8-fbcb-47d1-8600-d7a7742be1a2](./images/a6db7ad8-fbcb-47d1-8600-d7a7742be1a2.png)



## 挑战

做一个ghost blobe

看了下需求。感觉可以直接在基类上再叠一层就好。但是先做下消息显示和消失

![141247d2-4cd4-4eb0-87f5-ac097f8729ba](./images/141247d2-4cd4-4eb0-87f5-ac097f8729ba.png)



用蓝图做好折磨啊

感觉蓝图智能做一些很简单的逻辑。比如说设置percent啥的。当然也有我不咋会用蓝图的原因。

之前的游戏消息。我是搞了一个vertical的容器，将每一个消息widget塞进去了。然后在动画里设置透明度。动画播放完之后销毁



然后这个挑战。我是直接在base里重叠了一个ghost 然后设置其tick 每次interp 





## 正确的clamp数值

没看懂是什么意思啊

他这里在说什么PreAttributeChange是clamp了从modify获取的值??

我得问问了

这里好像都可以显示了。一个是

![811d2eec-6163-4777-9311-d6a40b6bbda3](./images/811d2eec-6163-4777-9311-d6a40b6bbda3.png)





## 第七章小结

这一张主要是学习了GT 。了解了ASC GE 本身可以携带GT 并且GE其实可以给ASC赋予GT 。



然后利用ASC的ApllyGEtoSelf委托来做了一个拾取道具显示信息的功能

其重点包括数据的流向。由ASC产生并且筛选出需要显示的tag和文本。文本是从自定义的datatable里来的

然后传给controller 传给widget完成UI的绘制



还有一个gost globe的功能其实就是在原本的globe下再加了一层。然后使用tick来进行finterp 还是比较简单。

这里教程没有讲清楚的坑就是baseValue和currentValue到底指的是什么以及pre和post两个函数究竟是怎么处理值的

我在知识点补充补充了



# 第八章

## 从dataTable配置初始属性值

创建了之前说的primaryValue 力量啥的

然后ASC里有一个配置初始属性表的地方

![4884bf44-c233-4cfb-8da8-c1ed680f3fa2](./images/4884bf44-c233-4cfb-8da8-c1ed680f3fa2.png)



表需要正确的表头

![995eff34-6b07-4eea-8ac5-8e142c32730e](./images/995eff34-6b07-4eea-8ac5-8e142c32730e.png)

这里的rowName需要是属性集名称.属性名

然后配置base属性就好

其实这玩意暂时的唯一作用就是设置初始值。了解一下吧。我感觉是使用GE要好点

![5f8786bb-b879-47e1-a4ee-b78c7d97c1af](./images/5f8786bb-b879-47e1-a4ee-b78c7d97c1af.png)



## 通过ge来初始化属性

在character里放一个uclass的ge 每个chracter可以有自己的初始化属性



对于属性的操作其实只在服务器上做就可以了。之前为什么需要在客户都安onrep_里也进行相关操作呢

因为那些是绑定委托。只有属性会网络复制。委托那些不会。所以一定是需要在客户端也做的。当然你在客户端设置属性也没问题。服务器会将其同步的



## 基于属性值的modifier

![d22199c0-03a0-4a5a-91db-513087867dae](./images/d22199c0-03a0-4a5a-91db-513087867dae.png)



这里可以选择依赖的属性。并且选择来源是source还是target  然后snap关系到这个数值是何时确定，是应用是确定还是发出时确定。大概是这个意思

![826e0ed1-a04e-4a0f-8468-23d80ce3c059](./images/826e0ed1-a04e-4a0f-8468-23d80ce3c059.png)



默认情况下他会加直接把获取到的back属性作为操作数



## 多个modifier之间的是实施顺序

基本原则是每个modifierhi根据顺序来执行的

![f84a47b2-2736-46df-8870-d65fb4b5753d](./images/f84a47b2-2736-46df-8870-d65fb4b5753d.png)





![161068aa-068d-4e83-8b81-b95290206c41](./images/161068aa-068d-4e83-8b81-b95290206c41.png)







![03a45f15-5d25-4352-a032-82099b631c22](./images/03a45f15-5d25-4352-a032-82099b631c22.png)



![f93907cf-557f-47c8-b119-e569f0b806b7](./images/f93907cf-557f-47c8-b119-e569f0b806b7.png)

## 修改系数

因为之前都是直接操作那个系数。比如说+- *  那如果想要0.1 *  str呢就需要用到系数了

![ecd8bc0b-bfab-4e46-a820-cf47743a2e87](./images/ecd8bc0b-bfab-4e46-a820-cf47743a2e87.png)



是这样的。还挺好理解。比如说post值就可以理解为基础伤害   pre的值暂时没想到那里可用

![4588c51e-4bc8-42a7-acd6-0976d163d489](./images/4588c51e-4bc8-42a7-acd6-0976d163d489.png)





![d0101f29-6f65-4c9d-9562-69e0d18d8e3a](./images/d0101f29-6f65-4c9d-9562-69e0d18d8e3a.png)



## 次要属性  部分或者全部依赖于其他属性

我们的primary属性 作为游戏的基础属性，不会被其他属性影响。只会保持自己的独立。然后可以被游戏机制加减。

然后secondary属性就是会依赖于primary属性表现出自己的值

这些都是游戏设计者自己决定的



所以其实和游戏进程更加直接相关的是secondary的属性值  

比如说暴击率 伤害 格挡率  最大生命值，最大魔力

他是这么设计的

![3e66c847-516e-486e-8f3c-93cf3f0096cb](./images/3e66c847-516e-486e-8f3c-93cf3f0096cb.png)



### 然后我设计的话

primary 是

| primary | secondary           | dependency |
| ------- | ------------------- | ---------- |
| str     | maxhealth           | str        |
| int     | max mana            | int        |
| luck    | phsical damage      | str        |
| def     | magic damage        | int        |
|         | critical chance     | luck       |
|         | critical damage     | luck       |
|         | health regeneration | str        |
|         | mana regeneration   | int        |
|         | block chance        | def        |



### 挑战

![7f79660c-fce5-4b76-a807-cb9cd2ee49bc](./images/7f79660c-fce5-4b76-a807-cb9cd2ee49bc.png)



## 设置依赖属性

即如果一个属性依赖于其他属性我希望这个属性能跟着被依赖属性一直变化

实现方式就是在游戏开始时初始化属性的时候就为其加上一个infinite的ge  这样是加了一个modifier就可以实现一直数据变化了



然后这个的原理其实就是之前提到的修改器。其不会tick执行什么的，只会在数值变换的时候进行修改



然后再possessed调用就好



### 挑战

完善自己的secondary属性的初始GE和依赖关系

![3b519d24-2a7f-4587-af6c-4d4b9dcd2252](./images/3b519d24-2a7f-4587-af6c-4d4b9dcd2252.png)

但是这里要注意，对secondary应用的是inifiniteoverride会导致其不能加base属性。只能借由依赖属性来变化数值



以及如果需要更加复杂的计算逻辑，比如说玩家所处的状态。那么就需要CMC 了 custom calculation class

## Custom culculation   MMC



比如说如果level不是一个属性，而是一个存在playerstate里的内容

但是我们最好不要依赖于具体的playerstate   不然如果获取怪物的level就还得放在character里。所以可以实现这样一个接口，因为我们是知道ge的target和source的

![94b3214f-d1e1-4260-b04e-7feb54676284](./images/94b3214f-d1e1-4260-b04e-7feb54676284.png)



![ebbc131d-50d2-4d27-b1dd-dfe6774268d0](./images/ebbc131d-50d2-4d27-b1dd-dfe6774268d0.png)



## 添加level 值player state 添加combat接口



然后由于level是我们自己定义了。而且需要显示到UI，所以我觉得得在playerstate加个委托然后widget controller绑定然后变化的时候广播



enemy有一点不同就是不用网络更新。只会在服务器上被设置

然后enemy也是同样的，不过属性值放在了character类上



接口实现可以放到character类上。放在都可以。反正GE触发时想要啥都能拿到



## 创建MMC



![e62f57f3-2d87-4ae6-9b86-ce2722a446b5](./images/e62f57f3-2d87-4ae6-9b86-ce2722a446b5.png)



然后重写这个函数，其返回值应该是需要被应用的值

![7cbb76bd-dffb-43e1-b424-eb744db89af3](./images/7cbb76bd-dffb-43e1-b424-eb744db89af3.png)

说是还要捕获一下数值。不知道干嘛的先看   他在构造函数中声明了想要捕获的属性

![748e4c85-e9a4-44ce-a9ef-cd14e88fa9f1](./images/748e4c85-e9a4-44ce-a9ef-cd14e88fa9f1.png)

然后还要选择是获取目标的还是来源的。以及指定是否快照。 然后加入一个捕获数组。这么说是不是可以捕获多个属性  是的，可以。不过每一个都要像第一个属性一样用一个变量来装

![46ed826c-358d-49c7-9883-716dde0d187b](./images/46ed826c-358d-49c7-9883-716dde0d187b.png)



不太理解他这个捕获tag的意义是何在![f10e6710-498d-4897-8b3e-30d1daf483f3](./images/f10e6710-498d-4897-8b3e-30d1daf483f3.png)



### 快照

我们可能实例化一个GE但是不马上应用他，比如说放到了一个火球术上。只有命中是才会应用。所以如果打开快照就会存储属性为创建的那一刻。否则是应用的时候现找



然后这里的sourcetag就是 一定需要存在的tag和如果存在就不执行的tag 两边都是   记得给cONTEXT加上source再去找source



**我知道了，因为之前这里这个标签应该是他自己捕获的，现在我们用自己的类了。也需要捕获标签来给他坐下判断**

![b0fee12a-ebf8-4200-b44b-3eccc5203611](./images/b0fee12a-ebf8-4200-b44b-3eccc5203611.png)

### 挑战

根据level 和智力设置max mana

![b697b976-9a0c-4f45-8d5a-e22397fdc8f3](./images/b697b976-9a0c-4f45-8d5a-e22397fdc8f3.png)



## 如何初始化血量和mana为max

因为max 依赖于其他属性。所以这里得看下咋搞

果然，直接用GE在前面的实施完成之后再实施

### 挑战

![8fb0373b-82bb-4562-9aa1-278a4980da43](./images/8fb0373b-82bb-4562-9aa1-278a4980da43.png)





## 第八章小结

比较有意思的一章。主要是讲了如何初始化AS

主要有三种方式

1 使用dataTable  目前仅能用来设置初始值。效果一般

2 使用GE 对于基础数值和vital数值可以使用instant但是对于依赖于其他的数值就需要使用infinite了

3 使用MMC进行计算。因为如果需要计算一个非属性值因素或者依赖于多个来源。那么普通的GE就比较难做了。用MMC可以自己设定计算公式



还添加了combat接口，以后所有的战斗内容都可以从接口里获取



中途由于添加属性那里。实在不想手写。去研究了一下接入Rider接入agent  
然后又去看了一下反射相关的内容耽误了一天半 ，现在继续

lua那些脚本语言，先等重要的核心都学完之后再搞吧，反正挺快的





# 第九章

## 属性值菜单



![ab498334-8e6a-447b-99d3-9fc804cd4d06](./images/ab498334-8e6a-447b-99d3-9fc804cd4d06.png)

### 然后就是做UI环节。跟着做就好

有一个namedSlot的空间。跟占位符的感觉差不多

如果继承了有namedslot的组件可以放自己的widget进去并且不破坏原有布局

![7ebd7b56-b57e-44a9-a29e-13113b4cd629](./images/7ebd7b56-b57e-44a9-a29e-13113b4cd629.png)



然后设置按钮的时候记得设置一下按下，悬浮，disable的几种样式



### 使用wrap box可以将组件一行行的排列

虽然我其实在想为什么不用vertical box



### 使用scroll box来做滚动框但是BOX需要被sizebox包裹，才知道自己的范围

超过划定的范围之后就会出现滚动条

### 如何在自定义button的内部设置onclied 并且让外部组件知道自己点击了

使用事件分发器 其实就是蓝图版的委托

![9ec7f6c1-5f71-4ca6-aec7-0823a4503c80](./images/9ec7f6c1-5f71-4ca6-aec7-0823a4503c80.png)

然后再外部本身也是依赖于内部的小组件。只是这样使用委托就是单项依赖而已  然后转化一下类型。来绑定委托

![f2fd7b02-7fb7-47a5-93e6-4085658ea08e](./images/f2fd7b02-7fb7-47a5-93e6-4085658ea08e.png)



### text有时候会阻挡button的点击

需要设置一下text

可见，但是不参与击中测试

![7156712b-87c7-4d3a-a1cc-4e599712c535](./images/7156712b-87c7-4d3a-a1cc-4e599712c535.png)





## 绑定属性值更新

首先是需要创建对应widget的对应controller然后使用一个委托的方式广播所有的属性变化。这样之后加属性就只用修改UI和dat asset就好

他好像是根据tag来进行联系的

![b2ea9fdd-80c0-461d-9960-412ced9bf4d6](./images/b2ea9fdd-80c0-461d-9960-412ced9bf4d6.png)



![3b2a47ad-dfbf-4d4a-8e5b-7d6fe8558805](./images/3b2a47ad-dfbf-4d4a-8e5b-7d6fe8558805.png)



![2f16156d-0870-463e-941d-adbf124200af](./images/2f16156d-0870-463e-941d-adbf124200af.png)



## 创建native gt

使用自己的单例，模式来添加了tag和GAS速成里边还不太一样。那边是通过namespace然后配合宏直接定义的



![71fcb0bd-553c-49a9-a2fa-3f9a74e6aa06](./images/71fcb0bd-553c-49a9-a2fa-3f9a74e6aa06.png)

![bbffeb54-c8d9-48be-b831-fb36fd3d41bf](./images/bbffeb54-c8d9-48be-b831-fb36fd3d41bf.png)

然后使用的话就需要我们创建一个FGamepolaytag变量 然后赋值

![2e7f4db8-fd78-424b-b67c-c3938b13bd61](./images/2e7f4db8-fd78-424b-b67c-c3938b13bd61.png)

之后就可以使用他了



## 添加asset Manager 单例 来管理自己资源的加载

![6b73e683-00db-418f-a2a6-444124c8f983](./images/6b73e683-00db-418f-a2a6-444124c8f983.png)



创建一个自己的单例类 然后重写游戏初始化虚函数

然后我们将自己的这个manager类设置为游戏的manager类

![45e7adbb-0962-4842-a8af-b7f1cf8efb8e](./images/45e7adbb-0962-4842-a8af-b7f1cf8efb8e.png)

指定Assetmanager的话需要配置配置文件，注意这里是项目名.类名

![0118e528-e780-40dc-bfd3-5ad40f3b96a4](./images/0118e528-e780-40dc-bfd3-5ad40f3b96a4.png)

### 挑战

创建所有的属性原生标签

![e261466d-e0db-4d48-a6da-c65f911c7e68](./images/e261466d-e0db-4d48-a6da-c65f911c7e68.png)







## 创建自定义AssetData结构体  然后创建AssetData

![e56a7af0-bfbf-4d68-a6a5-1e5cb4a4fa6f](./images/e56a7af0-bfbf-4d68-a6a5-1e5cb4a4fa6f.png)



![2b3fd554-09f8-4f3d-99d0-e0bc01a8ff95](./images/2b3fd554-09f8-4f3d-99d0-e0bc01a8ff95.png)



![d61f197d-3c2b-4d2c-bf9b-db07b531ee0f](./images/d61f197d-3c2b-4d2c-bf9b-db07b531ee0f.png)

![beaa5b50-03dc-41e0-bd8d-520c87426f54](./images/beaa5b50-03dc-41e0-bd8d-520c87426f54.png)

然后创建蓝图实例 在蓝图中直接编辑对应的结构体



## 创建widgetController

### 挑战

先自己创建widgetcontroller

![8301d893-4a75-43b4-b0b4-f0f03db21c18](./images/8301d893-4a75-43b4-b0b4-f0f03db21c18.png)



## 制作蓝图函数库  方便widget可以直接拿到controller而不用接HUD然后再找

![5acaee04-ab44-4db6-847a-d18d22f95cf0](./images/5acaee04-ab44-4db6-847a-d18d22f95cf0.png)

然后其中的函数都是static的，并且需要一个世界上下文对象。因为无法获取到World。都没有this指针

![e9c0e754-2466-4036-a87d-5e661ee84fad](./images/e9c0e754-2466-4036-a87d-5e661ee84fad.png)



## 挑战

创建新的函数获取asController

![b7236a35-e906-47b1-9884-98c22493b0df](./images/b7236a35-e906-47b1-9884-98c22493b0df.png)



注意，对于controller会用到的dataAsset是应该使用subclassof还是指针。主要是

关键区别在于你创建的是“DataAsset 对象资产”还是“继承自 DataAsset 的蓝图类”。  比如说dataTable DtatAsset这里。你创建的时候他都是让你选了类型的。其实就是创建了一个实际的对象而不是类型



## 为每个widget分配tag这样他们就知道自己应该匹配广播出来的哪一个数值

我怎么感觉可以再widgetbase上加上这个tag呢   是可以。但是对于那些纯文本的内容来说就多余了

还是从需要的基类里加吧



## 然后在AS中将属性值tag和gameplayAttribute绑定了起来

这样就可以通过轮询的方式将每一个属性的变化委托所绑定



然后通过tag找到对应的dataAsset里存储的信息  

最后通过attribute获取当前值



## 第九章小结

第九章主要是完成了属性值UI的制作

学习了nativeTag的增加，其主要就是GameplayManager.addNativetag

其中设置到了使用data table以及dataAsset来存储一些会经常修改的内容  自定义结构体内容

创建了新的controller其负责批量监听AS中的属性  ，依赖于AS构造函数中初始化tag以及attribute。相当于模板代码多了一步骤













































































































































--

# 知识点补充

## 什么时候需要使用UPROPERTY修饰指针

   背景： UE对于UObject采用自己的一套垃圾回收机制 GC 。 在每一个object对象创建时 ，UE都会将其加入一个全局管理对象数组。每隔一段时间UE都会扫描这数组判断哪些内容应该被回收 ，哪些内容依旧存货。
   回收依据：GC 通过UPROPERTY引用链去判断每一个对象。如果能够找到那么就认为存活，如果找不到则认为该回收。这里有一个很重要的点就是 其**不是根据引用计数来判断是否回收的** 这和C++的智能指针是两套方式  。

    如果我们使用裸指针或者智能指针修饰。那么C++知道这个对象还在用 。但是UE不知道，UE只要无法通过UPROPERTY找到这个对象那么就会将其释放导致野指针



   回到问题：我们什么时候需要使用UPROPERTY修饰指针 ？

    一句话来说就是：**如果该对象需要在离开作用域后跨帧存活。那么他就需要被UPROPERTY修饰**

            详细来说就是：GC的回收机制只有在游戏线程空闲的时候。可以理解为每一帧的中间时间才会激活。局部变量一定会在该函数中被使用完是不需要修饰的。



```
void AMyActor::SetupTimer(){ UMyObject* TempObj = NewObject<UMyObject>(this); // ⚠️ 把 TempObj 传给了一个延迟回调 // 函数结束后，没有 UPROPERTY 持有 TempObj // 下一次 GC 扫描时，TempObj 指向的对象就会被回收！ GetWorldTimerManager().SetTimer(TimerHandle, [TempObj]() { TempObj->DoSomething(); // 💥 可能已经是野指针 }, 1.0f, false);

}
```



比如说在这段代码里。 TempObj被lamda传入了。那么如果不使用UPROPERTY修饰下一次的时候就是野指针了  即使使用了shared_ptr 其也有可能会被GC回收的。标准做法时将其提升为成员变量并修饰



```
UPROPERTY()TArray<UMyObject*> Objects;

void AMyActor::AddObject(){ UMyObject* NewObj = NewObject<UMyObject>(this); Objects.Add(NewObj); // ✅ 加入后立即受 GC 保护}

void AMyActor::RemoveObject(int32 Index){ Objects.RemoveAt(Index); // ✅ 移除后 GC 不再保护，可被回收}
```





这一段代码演示了UE提供的TArray TMap之类的容器是如何保护其成员变量的  即当容器被标识UPROPERTY之后每次扫描时其内容也会被标识为存活    当然只有UE提供的容器有这种效果

## 不同的asc的复制模式

![9a7feeea-dd83-40f8-b74a-aa0de5f7cc31](./images/9a7feeea-dd83-40f8-b74a-aa0de5f7cc31.png)

## 游戏的单人多人必须在一开始就设计好   多人可以在单人情景游玩，但是单人没法多人游玩

## AcknowledgePossession 和OnRep_Controller

和OnRep_controlller类似都可以标记controller更改 但是这个是包括了处理完成了一系列前置工作



```

在客户端的网络流程中，执行顺序通常是：

Controller 变量同步。触发 OnRep_Controller。引擎内部执行 Super::AcknowledgePossession 逻辑（包括更新控制旋转、同步本地组件状态等）。执行你重写的 AcknowledgePossession 逻辑。如果你在 OnRep_Controller 中初始化逻辑，可能会遇到“变量虽然有了，但状态还没对齐”的情况（例如控制旋转没生效，或者某些依赖于 Controller 的 Subsystem 还没准备好
```



并且onrep在监听服务器上不会被执行 。使用AcknowledgePossession的话无论在哪里都会执行，这样可以避免判断是否是客户端还是服务器

AcknowledgePossession：无论是在纯客户端还是监听服务器的本地玩家身上，它都会被一致地调用。这让你的代码更具通用性，不需要为“我是不是服务器玩家”写额外的判断逻辑。

```



```示例代码
void AAuraCharacter::AcknowledgePossession(AController* NewController)
{
    Super::AcknowledgePossession(NewController); // 确保引擎完成内部关联

    // 此时初始化 GAS 或 输入映射是最稳妥的
    if (AbilitySystemComponent.IsValid())
    {
        AbilitySystemComponent->InitAbilityActorInfo(this, this);
    }
}
```

## 代码风格管理

接口或者说每一段代码以此来标识

![0e2a92a0-7845-4d35-a918-893b4ea659f2](./images/0e2a92a0-7845-4d35-a918-893b4ea659f2.png)

## mixed模式补充

![f7cf7aa5bcd94209a14bda726f39c3f9](/E:\UE5\NOTE\Aura/images/f7cf7aa5-bcd9-4209-a14b-da726f39c3f9.png)

主要就是说ability actor info 中的owner ，这个actor的owner必须是controller 在mix模式下  

如果actor  的owner不是character那么是需要手动设置为owner的

## ~ 游戏运行中调试命令行

### showdebug abilitysystem

可以显示玩家的attribute  按pagedown或者up 可以切换角色

## AttributeSet没有显性指定owner之类的。其怎么知道自己是哪个character的属性呢

以及我还有个问题是

ASC倒是调用了函数initActorInfo来设置owner但是attribute没有啊。他是怎么识别自己的owner是谁的

```

    在 Unreal Engine 的 Gameplay Ability System (GAS) 中，这是一个非常经典且巧妙的设计。

    简单直接的结论是：不是 AttributeSet 主动寻找 Character，而是 AbilitySystemComponent (ASC) 在初始化阶段主动“扫描”并发现了属于同一个 Actor 的 AttributeSet。

    以下是底层的 C++ 实现机制和逻辑拆解：

    1. 自动注册机制：InitializeComponent
    当你在 APlayerState 的构造函数中通过 CreateDefaultSubobject 创建了 AbilitySystemComponent 和 AttributeSet 时，它们都属于同一个 Outer（即这个 PlayerState 实例）。

    在游戏启动或 Actor 生成时，ASC 的 InitializeComponent() 虚函数会被调用。在这个函数内部，GAS 实现了一套自动搜索逻辑：

    遍历子对象：ASC 会获取它的 GetOwner()（即 PlayerState）。
    查找 AttributeSet：它会利用 Unreal 的反射机制遍历所有属于该 Owner 的子对象（Subobjects）。
    注册到 SpawnedAttributes：如果发现任何类型为 UAttributeSet 的子对象，ASC 会自动将其添加到自己的 SpawnedAttributes 数组中，并完成内部绑定。
    这就是为什么你不需要手动把 AttributeSet 指针传给 ASC，只要它们都在同一个 Actor 下创建，ASC 就能“看见”它。

    2. InitActorInfo 的真正作用
    你可能会问：“既然 ASC 已经找到了 AttributeSet，为什么我还要在 Character 里调用 InitActorInfo？”

    这是因为 实例化（Instantiation） 和 逻辑关联（Linking） 是两回事：

    实例化阶段：ASC 仅仅是知道了“我手头有一个 AttributeSet 可以用来存取数值”。但此时它还不知道这个数值是给谁用的（AvatarActor 是谁），也不知道谁在控制（OwnerActor 是谁）。
    InitActorInfo 阶段：当你调用这个函数并传入 APlayerState 和 ACharacter 时，ASC 会更新内部的 FGameplayAbilityActorInfo 结构体。
    分发信息：一旦 InitActorInfo 被调用，ASC 会遍历它已经发现的所有 AttributeSet，并确保它们都能访问到这份最新的 ActorInfo。
    3. AttributeSet 如何获取 Character？
    在 UAttributeSet 的子类逻辑中（例如 PostGameplayEffectExecute），你经常会看到这样的代码：

    C++
    FGameplayEffectModCallbackData Data;
    AActor* TargetAvatar = Data.Target.GetAvatarActor();
    这里的 Data.Target 就是 AbilitySystemComponent。由于你之前调用了 InitActorInfo(PlayerState, Character)，ASC 内部已经保存了 Character 的指针。AttributeSet 只需要问它的“管理者”（ASC）：“我们的 AvatarActor 是谁？”，就能拿到对应的 Character。

    4. 总结：对象关系链
    所有权关系：PlayerState 拥有 ASC 和 AttributeSet（通过 CreateDefaultSubobject）。
    管理关系：ASC 在启动时通过扫描 Outer 自动将 AttributeSet 纳入管理范围。
    数据链路：当你执行 “灵魂（PlayerState）注入肉体（Character）” 的操作（即调用 InitActorInfo）时，这条链路被激活，AttributeSet 里的数值才真正与屏幕上的 Character 产生逻辑关联。
    注意： 如果你在运行期间动态添加 AttributeSet，通常需要使用 ASC->GetSet<UYourAttributeSet>()，这个方法会自动处理创建和注册过程，以确保 ASC 能够识别它。而在构造函数中使用 CreateDefaultSubobject 是针对预定义属性集的标准做法。
```

那么问题来了OUTER是什么

看了一下。所以说之前为什么局部的变量不能作为WorldContext去找到world啊。因为局部的没有outer没法向上

```

在 Unreal Engine 的 C++ 架构中，Outer（外部对象） 是一个非常核心的概念，它是 UObject 系统实现“父子关系”和“所有权逻辑”的基石。

你可以把 Outer 理解为对象的“归属者”或“容器”。

1. 核心定义：什么是 Outer？
每一个从 UObject 派生的类实例，内部都有一个名为 OuterPrivate 的指针。这个指针指向“拥有”这个对象的另一个对象。

所有权层级：在 UE 中，对象不是孤立存在的，它们形成了一个树状结构。例如：
Level 的 Outer 是 World。
Actor 的 Outer 是 Level。
ActorComponent 的 Outer 是 Actor。
AttributeSet 的 Outer 是 PlayerState（在你的代码例子中）。
2. 在代码中是如何确定的？
当你使用 CreateDefaultSubobject 或 NewObject 时，系统会显式或隐式地设置 Outer。

构造函数中 (CreateDefaultSubobject)
在你提供的代码片段里：

C++
// 在 APlayerState 的构造函数中
AttributeSet = CreateDefaultSubobject<UAuraAttributeSet>(TEXT("AttributeSet"));



`CreateDefaultSubobject` 是 `UObject` 的一个成员函数。当你直接调用它而不指定父对象时，它会**自动将当前对象（即 `this`，你的 PlayerState 实例）设为新创建对象的 Outer**。

#### 运行时 (NewObject)

如果你在运行时手动创建对象：

// 显式指定 Outer 为 this
UMyObject* Obj = NewObject<UMyObject>(this, UMyObject::StaticClass());
第一个参数就是 `Outer`。



3. Outer 的三大作用

#### A. 内存管理与垃圾回收 (GC)

UE 的垃圾回收器会遍历对象图。如果一个对象没有被标记为 `UPROPERTY` 引用，但它有一个合法的 Outer，并且它的 Outer 正在被引用或处于活跃状态，这有助于 GC 理解对象之间的生命周期依赖关系。通常，如果 Outer 被销毁，其所属的 Subobjects 也会被标记为待销毁。

#### B. 路径与寻址 (Object Path)

UE 中的每个对象都有一个唯一的路径，格式类似于：`/Game/Maps/MyLevel.MyLevel:PersistentLevel.MyPlayerState.AttributeSet`这个路径就是通过不断回溯 `GetOuter()` 直到根部（通常是 Package）构建出来的。

#### C. 获取环境上下文 (World Context)

这是最实用的功能。很多 `UObject` 本身并没有 `GetWorld()` 的能力，但它们可以通过 Outer 来“借”一个 World。例如，`UAttributeSet` 内部并没有保存 World 指针，但当你调用 `GetWorld()` 时，它会调用：

UWorld* UObject::GetWorld() const {
    if (Outer) return Outer->GetWorld(); // 递归向上找，直到找到 Actor 或 Level
    return nullptr;
}

4. 回到 GAS 的例子



在你的代码里，`AbilitySystemComponent` 和 `AttributeSet` 的 **Outer 都是同一个 PlayerState**。

当 `AbilitySystemComponent` 初始化时，它执行了类似这样的逻辑：

1. **“谁是我的 Outer？”** -> 得到 `PlayerState`。
2. **“我的 Outer 还有哪些其他的子对象（Subobjects）？”**
3. 通过反射遍历 `PlayerState` 下属的所有对象，发现：“嘿，这儿有一个 `UAuraAttributeSet` 类型的对象，它的 Outer 也是 PlayerState！”
4. **“把它加入我的管理列表。”**

**总结：**`Outer` 就像是对象的“户口本”，它定义了你属于谁。正是因为它们都在同一个“户口本”（PlayerState）下，ASC 才能轻松地在同一个家里找到 AttributeSet。CreateDefaultSubobject 是 UObject 的一个成员函数。当你直接调用它而不指定父对象时，它会自动将当前对象（即 this，你的 PlayerState 实例）设为新创建对象的 Outer。

运行时 (NewObject)如果你在运行时手动创建对象：

C++// 显式指定 Outer 为 thisUMyObject* Obj = NewObject<UMyObject>(this, UMyObject::StaticClass());第一个参数就是 Outer。

3. Outer 的三大作用A. 内存管理与垃圾回收 (GC)UE 的垃圾回收器会遍历对象图。如果一个对象没有被标记为 UPROPERTY 引用，但它有一个合法的 Outer，并且它的 Outer 正在被引用或处于活跃状态，这有助于 GC 理解对象之间的生命周期依赖关系。通常，如果 Outer 被销毁，其所属的 Subobjects（子对象）也会被标记为待消除（Elimination）。

B. 获取环境上下文 (World Context)这是最实用的功能。很多 UObject 本身并没有直接存储 World 指针，但它们可以通过 Outer 来“借”一个 World。 例如，当你对一个 UObject 调用 GetWorld() 时，它的默认逻辑是：

C++UWorld* UObject::GetWorld() const { if (Outer) return Outer->GetWorld(); // 递归向上找，直到找到 Actor 或 Level return nullptr;}这使得 AttributeSet 即使不是 Actor，也能通过 Outer（PlayerState）访问到当前的关卡世界。

C. 系统发现 (Discovery)回到你之前的疑惑：ASC 怎么知道 AttributeSet 在哪里？ 因为它们共享同一个 Outer。ASC 内部会调用 GetOuter() 拿到 PlayerState，然后搜索 PlayerState 旗下所有的子对象。如果发现某个子对象的 Outer 是这个 PlayerState 且类型匹配，它们就被关联起来了。

4. 总结Outer 就像是对象的“户口本”，它定义了你属于谁。正是因为 AttributeSet 的 Outer 被自动设为了 PlayerState，它才会被纳入该 Actor 的生命周期和系统管理之中。



```





## xx::StaticClass()

和下面一小节一起食用。在UE中为了很多的功能需求引入了反射概念。

每一个写的c++类只要其内部有generated_BODY这个宏。
那么在引擎启动早期就会对每一个类生成一个UClass实例 这个实例不同于真正的类对象 其只是标记了很多类应该有的内容



而staticclass就会返回这一个class对象 比如说用来创建类对象的时候用

```
在 Unreal Engine C++ 中，UAttributeSet::StaticClass() 返回的是一个指向 UClass 对象 的指针（即 UClass*）。

要理解它的本质，我们需要从 Unreal 的反射系统（Reflection System）说起：

1. 核心定义：什么是 UClass？
在标准 C++ 中，类（Class）只是一种编译时结构。程序运行后，编译器并不保留关于“类”本身的详细信息。

Unreal 为了实现编辑器交互、蓝图支持、垃圾回收和序列化，引入了反射系统。对于你写的每一个 UCLASS，引擎在程序启动时都会自动创建一个对应的 UClass 实例。这个实例就像是一个“元数据手册”，记录了：

这个类的名字叫什么？
它的父类是谁？
它有哪些被 UPROPERTY 标记的变量？
它有哪些被 UFUNCTION 标记的函数？
2. StaticClass() 到底返回了什么？
StaticClass() 是由 GENERATED_BODY() 宏自动生成的静态函数。它返回的就是上面提到的那个唯一的 UClass 元数据对象。

返回类型：UClass*。
唯一性：对于 UAttributeSet 这个类，整个引擎运行期间只有一个 UClass 实例代表它。
本质：它代表的是“类型本身”，而不是某个具体的属性集实例（对象）。
3. StaticClass() 与 GetClass() 的区别
这是开发者最容易混淆的两个概念：

UAttributeSet::StaticClass()：静态调用。意思是：“我要获取代表 UAttributeSet 这个类型的元数据。”（不需要具体对象也能调用）。
MyAttributeInstance->GetClass()：实例调用。意思是：“我要看 MyAttributeInstance 这个具体的活对象到底是什么类型的。”
举例说明： 如果你在蓝图中继承了 UAttributeSet 命名为 BP_AuraAttributeSet。

在 C++ 里调用 UAuraAttributeSet::StaticClass()，你会得到 C++ 类的元数据。
如果你拿到那个蓝图的实例并调用 GetClass()，你会得到代表蓝图类的 UClass 指针。
4. 为什么要用它？
你在开发中经常会在以下三个场景用到它：

A. 类型判定 (IsA)
检查一个对象是不是某个类或其派生类：

C++
if (MyObject->IsA(UAttributeSet::StaticClass())) 
{
    // 这是一个属性集或其派生类
}
B. 创建对象

像 `NewObject` 这样的工厂函数需要知道你想创建什么类型：
// NewObject 的默认参数通常就是 T::StaticClass()
UAttributeSet* NewSet = NewObject<UAttributeSet>(Outer, UAttributeSet::StaticClass());
C. 在蓝图中限制类型
当你定义一个 `TSubclassOf` 变量时，底层其实就是在存储 `UClass*`，而 `StaticClass()` 常用于初始化或对比这些变量：

UPROPERTY(EditAnywhere)
TSubclassOf<UAttributeSet> AttributeClass;

// 在代码中赋值
AttributeClass = UAuraAttributeSet::StaticClass();

5. 它是怎么生成的？

当你编译项目时，**Unreal Header Tool (UHT)** 会扫描你的头文件。如果你写了 `GENERATED_BODY()`，它会在对应的 `.generated.h` 和 `.gen.cpp` 文件中生成类似这样的代码（简化版）：

// 在生成的代码中
UClass* UAttributeSet::StaticClass()
 {
    static UClass* Singleton = nullptr;
    if (!Singleton)
    {
        Singleton = GetPrivateStaticClass(TEXT("AttributeSet"));
    }
    return Singleton;
}


这种单例模式确保了全局范围内，每个类对应的 `UClass` 只有一个，从而实现高效的运行时类型识别（RTTI）。B. 创建对象像 NewObject 这样的工厂函数需要知道你想创建什么“模版”：

C++// 创建一个 UAttributeSet 类型的对象// 第二个参数其实就是 UClass* 类型UAttributeSet* NewSet = NewObject<UAttributeSet>(Outer, UAttributeSet::StaticClass());C. 在蓝图中限制类型选择当你定义一个 TSubclassOf<T> 变量时，它底层存储的就是 UClass*。你可以用 StaticClass() 给它赋值：

C++UPROPERTY(EditAnywhere)TSubclassOf<UAttributeSet> AttributeClass;

// 在代码中初始化为特定的类AttributeClass = UAuraAttributeSet::StaticClass();5. 它是怎么生成的？当你编译项目时，Unreal Header Tool (UHT) 会扫描你的头文件。如果你写了 GENERATED_BODY()，它会在对应的 .gen.cpp 文件中生成一段代码。这段代码会确保在引擎启动阶段（早于 BeginPlay），这个 UClass 单例就被创建并注册到全局类型数据库中。

总结： StaticClass() 是你访问 Unreal 反射系统的门票，让你能在运行时像操作数据一样操作“类类型”。
```



## UClass 与反射系统



```
这种单例模式确保了全局范围内，每个类对应的 `UClass` 只有一个，从而实现高效的运行时类型识别（RTTI）。B. 创建对象像 NewObject 这样的工厂函数需要知道你想创建什么“模版”：

是的，你的理解非常准确。TSubclassOf<T> 在本质上就是一个经过类型安全包装的 UClass* 指针，它指向的就是你所说的元对象（Meta-Object）。

我们可以从以下几个维度来深度理解它：

1. 它确实指向元对象在 Unreal 中，UClass 实例就是描述类信息的元对象。

UClass* 指向的是“类本身”。TSubclassOf<AActor> 指向的也是“类本身”，但它在编译器层面加了一个约束：这个类必须是 AActor 或其派生类。2. 为什么不直接用 UClass*？如果你在代码里写：

C++UPROPERTY(EditAnywhere)UClass* ClassToSpawn;在编辑器里，下拉列表会显示引擎中所有的类（成千上万个），包括光源、材质、声音等，这会导致数据填写的混乱和崩溃风险。

如果你使用：

C++UPROPERTY(EditAnywhere)TSubclassOf<ACharacter> CharacterClass;编辑器过滤器：下拉列表会自动过滤，只显示 ACharacter 及其子类（如 BP_PlayerCharacter）。这就是你提到的“元对象继承于指定的父类”。

3. 类型安全与编译期检查TSubclassOf 在 C++ 层面提供了保护。它利用模板在编译时进行检查：

C++TSubclassOf<UAttributeSet> AttrClass;

// 正确：UAuraAttributeSet 继承自 UAttributeSetAttrClass = UAuraAttributeSet::StaticClass();

// 编译报错：AActor 并没有继承自 UAttributeSet// AttrClass = AActor::StaticClass();4. 它与实例的关系 (关键区别)这是最容易搞混的地方，请记住这个公式：

TSubclassOf<T> = “图纸”（它是元对象，描述了如何制造一个对象，但它不是对象本身）。T* (如 ACharacter*) = “实物”（它是已经根据图纸制造出来的、存在于世界中的个体）。在你的 PlayerState 例子中：

你实例化 UAuraAttributeSet 是为了得到一个实物来存储血量数据。而如果你想在某个地方设置“我们要生成哪种类型的技能特效”，你会用 TSubclassOf<ANiagaraActor> 来存储那张图纸。5. 运行时转换虽然它包装了元对象，但你随时可以把它当做普通 UClass* 使用，比如配合 SpawnActor：

C++UPROPERTY(EditAnywhere)TSubclassOf<AActor> ClassToSpawn;

// ... 在某个函数里 ...// 引擎会根据 ClassToSpawn 指向的元对象（图纸），在世界上生成一个实物（实例）AActor* NewActor = GetWorld()->SpawnActor<AActor>(ClassToSpawn);


    ## getClass 和 xx::StaticClass区别




UAttributeSet::StaticClass()：静态调用。意思是：“我要获取代表 UAttributeSet 这个类型的元数据。”（不需要具体对象也能调用）。MyAttributeInstance->GetClass()：实例调用。意思是：“我要看 MyAttributeInstance 这个具体的活对象到底是什么类型的。”这两个是不是获取的都是uclass只不过一个是静态调用 一个是从实际的类对象调用是的，你的理解完全正确。它们最终指向的都是同一个 UClass 元对象。

我们可以从以下两个层面来拆解它们的相同点与细微差别：

1. 结果的同一性在内存中，每一个类（无论是在 C++ 定义的还是在蓝图中创建的）都只有一个唯一的 UClass 实例。

假设你有一个 C++ 类 UAuraAttributeSet：

调用 UAuraAttributeSet::StaticClass() 返回的是指针 A。如果你有一个 UAuraAttributeSet 的实例对象 MyInstance，调用 MyInstance->GetClass() 返回的也是指针 A。此时，(UAuraAttributeSet::StaticClass() == MyInstance->GetClass()) 的结果为 True。

2. 核心区别：编译时确切性 vs 运行时多态性这是它们在开发中最关键的区别：

StaticClass() —— “我知道我要什么类型”它是硬编码的。你在写代码时就已经明确知道你要引用哪个特定的类元数据。

用途：用于类型转换（Cast）、类型判定（IsA）、或者指定工厂函数（NewObject）要生成的模板。局限性：它无法感知子类。如果你对父类调用 StaticClass()，你永远只能拿到父类的元数据。GetClass() —— “我要看你实际上是什么”它是动态的。它支持 C++ 的多态性。

用途：当你拿到一个父类指针（比如 UAttributeSet*），但你想知道它在运行时的真实身份时使用。威力所在：如果你的 UAuraAttributeSet 被玩家在蓝图中继承并改名为 BP_AuraAttributeSet_C：UAuraAttributeSet::StaticClass() 依然返回 C++ 父类的元数据。MyInstance->GetClass() 则会返回那个蓝图子类的元数据。3. 类比理解StaticClass() 像是“按名索骥”：你翻开《百科全书》的“猫科”这一页，查看关于猫的定义。GetClass() 像是“实地考察”：你面前走过来一只动物，你检查它脖子上的挂牌，看它到底是“波斯猫”还是“老虎”。4. 在 GAS 开发中的实际应用在你的代码语境下，这种区别非常重要：

C++// 场景 A：创建对象// 你明确知道要创建一个 UAuraAttributeSet 类型的实物AttributeSet = CreateDefaultSubobject<UAuraAttributeSet>(TEXT("AttributeSet"));

// 场景 B：处理 GameplayEffect 改变void UMySet::PostGameplayEffectExecute(const FGameplayEffectModCallbackData& Data){ // Data.Target 是 ASC // 我们不知道这个 ASC 是属于什么类的实例（可能是 PlayerState 的，也可能是某个小怪的） UClass* ActualClass = Data.Target->GetClass(); // 如果我们想判断它是不是某种特殊的 ASC if (ActualClass->IsChildOf(UMySpecialAbilitySystemComponent::StaticClass())) { // 逻辑处理 }

}

```







## getClass 和 xx::StaticClass区别



```
UAttributeSet::StaticClass()：静态调用。意思是：“我要获取代表 UAttributeSet 这个类型的元数据。”（不需要具体对象也能调用）。MyAttributeInstance->GetClass()：实例调用。意思是：“我要看 MyAttributeInstance 这个具体的活对象到底是什么类型的。”这两个是不是获取的都是uclass只不过一个是静态调用 一个是从实际的类对象调用是的，你的理解完全正确。它们最终指向的都是同一个 UClass 元对象。

我们可以从以下两个层面来拆解它们的相同点与细微差别：

1. 结果的同一性在内存中，每一个类（无论是在 C++ 定义的还是在蓝图中创建的）都只有一个唯一的 UClass 实例。

假设你有一个 C++ 类 UAuraAttributeSet：

调用 UAuraAttributeSet::StaticClass() 返回的是指针 A。如果你有一个 UAuraAttributeSet 的实例对象 MyInstance，调用 MyInstance->GetClass() 返回的也是指针 A。此时，(UAuraAttributeSet::StaticClass() == MyInstance->GetClass()) 的结果为 True。

2. 核心区别：编译时确切性 vs 运行时多态性这是它们在开发中最关键的区别：

StaticClass() —— “我知道我要什么类型”它是硬编码的。你在写代码时就已经明确知道你要引用哪个特定的类元数据。

用途：用于类型转换（Cast）、类型判定（IsA）、或者指定工厂函数（NewObject）要生成的模板。局限性：它无法感知子类。如果你对父类调用 StaticClass()，你永远只能拿到父类的元数据。GetClass() —— “我要看你实际上是什么”它是动态的。它支持 C++ 的多态性。

用途：当你拿到一个父类指针（比如 UAttributeSet*），但你想知道它在运行时的真实身份时使用。威力所在：如果你的 UAuraAttributeSet 被玩家在蓝图中继承并改名为 BP_AuraAttributeSet_C：UAuraAttributeSet::StaticClass() 依然返回 C++ 父类的元数据。MyInstance->GetClass() 则会返回那个蓝图子类的元数据。3. 类比理解StaticClass() 像是“按名索骥”：你翻开《百科全书》的“猫科”这一页，查看关于猫的定义。GetClass() 像是“实地考察”：你面前走过来一只动物，你检查它脖子上的挂牌，看它到底是“波斯猫”还是“老虎”。4. 在 GAS 开发中的实际应用在你的代码语境下，这种区别非常重要：

C++// 场景 A：创建对象// 你明确知道要创建一个 UAuraAttributeSet 类型的实物AttributeSet = CreateDefaultSubobject<UAuraAttributeSet>(TEXT("AttributeSet"));

// 场景 B：处理 GameplayEffect 改变void UMySet::PostGameplayEffectExecute(const FGameplayEffectModCallbackData& Data){ // Data.Target 是 ASC // 我们不知道这个 ASC 是属于什么类的实例（可能是 PlayerState 的，也可能是某个小怪的） UClass* ActualClass = Data.Target->GetClass(); // 如果我们想判断它是不是某种特殊的 ASC if (ActualClass->IsChildOf(UMySpecialAbilitySystemComponent::StaticClass())) { // 逻辑处理 }

}


```

## 客户端会初始自己的本地controller但是服务器也会初始controller并且复制回客户端那么客户端会谁的

这就涉及到controller在多人联机时的初始化顺序

所以可以看到onreo_pc 其实只是服务器上分配到了controller的通知，在本地controller其实早已就绪 只是没法从pawn上获取

```
时序对比``` 
客户端本地时间线：

[连接建立]
    ↓
PlayerController 已存在 ✅  ← 不依赖 RepNotify，连接时直接创建
    ↓
[地图加载/游戏开始]
    ↓
Pawn Spawn 并复制过来
    ↓
OnRep_Controller 触发     ← Pawn 得知自己的 Controller
    ↓
PlayerState 复制过来
    ↓
OnRep_PlayerState 触发    ← Pawn 得知自己的 PlayerState
```

所以回到你上一个问题
这就解释了为什么在 OnRep_PlayerState 时 PlayerController 通常是有效的：
PC 在连接建立时就创建好了，是最早就绪的对象之一
OnRep_PlayerState 触发时 PC 大概率已经存在
但仍然说"不一定"，是因为：
OnRep_Controller（Pawn 上的 Controller 指针被赋值）和 OnRep_PlayerState 的顺序没有严格保证——PC 对象本身存在，但 Pawn 的 Controller 指针不一定已经指向它了



## HUD的初始顺序

HUD是在pc 的beginplay里是初始化的 而且只在本地初始化  所以很早就准备就绪了。  在onrep里使用是没有问题的



```
客户端时间线：

[连接建立] → PC 创建
    ↓
PC.BeginPlay() → HUD 自动创建 ✅
    ↓
Pawn 复制过来
    ↓
OnRep_Controller
    ↓
OnRep_PlayerState  ← 此时 HUD 早就存在了

```



## UCLASS()说明符无法被继承

比如说我们在做UI的蓝图绑定委托的时候，是需要转换到具体的controller来绑定委托的   但是controller的子类都得自己写上标识符才行 无法继承父类的标识符

## 组件蓝图中的眼睛和isvariable



```
准确的区分
👁️ 小眼睛（Instance Editable）
控制的是：能否在放置实例时，直接在 Details 面板里编辑这个变量的默认值
比如你把 Widget A 嵌套放入 Widget B 的 Designer 中
如果 Widget A 里某个 float 变量开了眼睛
那么在 Widget B 的 Designer 里选中 Widget A，右侧 Details 面板就能直接改那个 float 的值
本质是编辑器层面的实例定制，跟运行时访问无关
☑️ Is Variable
控制的是：这个控件（ProgressBar/Button等）是否作为一个变量，暴露到蓝图事件图表中
勾选后，你才能在 Event Graph 里 Get 到这个控件
本类自身 和 子类 都能访问
不勾选的话，这个控件只存在于 Designer 布局中，无法在任何蓝图逻辑中引用
```



## GE的堆叠策略是如何计算的



```
你的理解非常准确。这正是 GAS 处理“多实例”与“单实例堆叠”的核心区别。为了让你彻底理清逻辑，我们可以把这两种情况拆解对比：

情况 A：不开启堆叠（独立实例）
如果你对目标施加了 3 次同一个 GE，且该 GE 没有开启 Stacking：

实例数量：目标身上会有 3 个独立 的 GE 实例。
数值计算：每个实例都会运行自己的周期计时器（Period Timer）。在每一秒结束时，3 个实例分别触发一次 -5 的效果。总表现为一秒内扣了 5 + 5 + 5 = 15 滴血。
时间计算：完全独立。
实例 1 在第 1 秒施加，第 5 秒结束。
实例 2 在第 2 秒施加，第 6 秒结束。
它们互不影响，各自到期后自我消除（Eliminate）。
情况 B：开启堆叠（单实例计数）
如果你开启了 Stacking（以 Aggregate by Target 为例）：

实例数量：目标身上只会存在 1 个 该 GE 的实例，但它的 StackCount（层数）变量变为了 3。
数值计算：系统只有一个计时器在跑。每隔一秒，系统查看当前层数（3），执行逻辑为：单层数值(-5) * 层数(3) = -15。
时间计算：由堆叠政策统一管理。此时你看到的 Stacking 设置项就开始起作用了：

1. 持续时间如何依托设置？
   在堆叠设置里，你可以决定新的一层进来时，这“一个实例”的寿命怎么算：

Refresh Duration（刷新持续时间）：只要新加一层，整个 GE 的剩余时间重置为最大值（比如总长 5 秒，在第 4 秒加了一层，它又变回 5 秒）。
Never Refresh（从不刷新）：第一个 GE 什么时候过期，整个堆叠就什么时候一起消失，不管中途加了多少层。
2. 周期计时器（Period）的特殊处理
这里有一个容易被忽略的设置：Stack Period Reset Policy（堆叠周期重置政策）。

Reset Period on Stacking（堆叠时重置周期）：每当加一层堆叠，每秒扣血的那个“1秒闹钟”就重新开始计时。
风险：如果玩家手速极快，在 0.9 秒时加了一层，闹钟重置，可能导致这 15 滴血迟迟扣不出来（因为始终跑不满 1 秒）。
Never Reset（从不重置）：闹钟照常跑。不管你中间怎么加层数，每到整秒就按当时的层数扣血。这是最常用的设置。
总结对比表
特性    不堆叠 (3个GE)    开启堆叠 (3层)
计时器    3 个闹钟独立跑    1 个闹钟跑
数值    3 次独立的 -5    1 次合并的 -15
到期消除    各过各的，分批消失    根据政策，要么一起消失，要么层数逐层递减
性能    较高（实例多）    较低（节省资源）
结论：你的理解是正确的。开启堆叠后，数值确实是 层数 * 基础值，而时间的生命周期则完全交由 GE 蓝图中的 Stacking 策略 来定义。如果你希望模拟那种“每个 GE 独立计算时间，但数值叠加”的效果，通常会使用 Stack Expiration Policy 设置为 Remove Single Stack（到期只减一层，而不是全部消除）。



```





## UE的广播策略

默认是同步的，所以不需要担心局部变量的问题

```
2. 广播机制（同步 vs 异步）
在 Unreal Engine 中，Broadcast 调用默认是同步（Synchronous）执行的。

当执行 Broadcast(OutContainer) 时，程序会立即顺序执行所有绑定在该委托上的回调函数。

在所有监听器执行完毕之前，CPU 不会返回这行代码的下一句。因此，在监听器函数执行的整个时间窗口内，OutContainer 都在栈上稳稳地存活着，数据完全有效。
```

## UE的widget的填充策略都有什么区别

![faab5893-1bbf-4d64-ab4a-c96a1a222aaa](./images/faab5893-1bbf-4d64-ab4a-c96a1a222aaa.png)



```
在 Unreal Engine 的 UMG 设计器界面中，右上角的 填充模式（Fill Screen / Custom / Desired / Custom on Screen） 主要用于控制在编辑器内如何预览你的 UI 布局。

这些设置仅影响编辑器内的预览效果，不会改变 Widget 在运行时的实际逻辑尺寸（运行时的尺寸由父容器的 Slot 属性或 DPI 缩放决定）。以下是各模式的详细区别：

1. Fill Screen (填充屏幕)
概念：模拟 Widget 占据整个玩家视口的状态。
用途：最常用的模式，用于设计主菜单、HUD 等全屏显示的界面。
特点：你会看到一个预设的分辨率边框（如 1920x1080）。在此模式下，你可以测试 Anchors (锚点)。当你手动拖动预览窗口大小时，Widget 会根据锚点设置自动偏移或拉伸，帮助你检查不同屏幕比例下的排版是否正常。
2. Custom (自定义)
概念：允许你手动输入具体的宽度和高度（以 Slate 单位为准）。
用途：当你设计的是一个具有固定尺寸的组件（如一个特定大小的物品栏方块）时使用。
特点：界面会根据你输入的数值强制显示一个矩形区域。这对于设计那些将来会被放入 Size Box 或具有固定尺寸要求的 UI 模块非常有用。
3. Desired (所需尺寸)
概念：预览区域的大小完全由 Widget 内部子控件的“理想大小”决定。
用途：用于设计高度动态的组件，例如一个会根据文字长度自动伸缩的对话气泡。
特点：预览窗口会自动紧贴你的内容边缘。如果你的内容增加（比如在 Text 控件里多打几个字），预览框会随之变大。它能让你直观看到这个组件“最自然”的状态。
4. Custom on Screen (屏幕上的自定义)
概念：这是 Fill Screen 和 Custom 的结合体。
用途：用于预览一个小比例组件在全屏视口中占多少位置。
特点：它会显示一个完整的全屏背景（通常是暗色的），并在其中间或指定位置显示你设置好的 Custom 尺寸区域。这有助于你感知一个小部件在整个游戏画面中的视觉比例。
核心开发建议
锚点测试：在 Fill Screen 模式下，务必利用左上角的 Screen Size 下拉菜单切换不同的设备（如 iPhone、Steam Deck、16:9 电脑显示器），观察界面是否发生重叠或超出屏幕。如果发生错误，应通过调整锚点或使用 Overlay/Grid Panel 来“消除”布局崩溃的风险。
模块化设计：如果你在制作可复用的子部件（User Widget），建议切换到 Desired 模式。这样当你把这个子部件拖入主 HUD 时，它能正确地向父容器报告自己所需的空间。
DPI 缩放：无论你在预览中看到的大小如何，记得在 Project Settings > User Interface > DPI Scaling 中检查缩放曲线，确保在高分辨率下 UI 不会变得过小。
```



## Attribute set中的CurrentValue 和Base Value的区别

简单来说：baseValue是固定的数值。比如说升级+基础生命+instant效果（包含duration但是设置了周期的效果）一起加起来的值



currentValue是infinite durtation但是没有设置周期的GE设置的效果。比如说生命值临时增加100 。这个效果其实是在AS里留下了一系列modifier即修改器
我们最终看到的Value 都是base+modifier计算出来的



既然instant作用于base我这里就有一个问题是

那比如说一个将现有生命值乘以1.2的无限效果。base生命值为100、显示会有120.但是由于造成伤害是instant的，作用于base,那不是造成100点base伤害就变成了0*1.2 = 0导致角色死亡?  
    实际上如果这个GE作用于Health那么确实会导致死亡。所以一般这种GE的会作用到Max上 对health上只应用instant的。然后最大生命值减少时对health做一下clamp就好让其不要超过最大值



## PreAttributeChange和PostGameplayEffectExecute的区别



在PreAttributeChange中我们修改Newvalue  这个value其实只会影响后续使用他的值。比如说数值变化的委托。但是对于basevalue的更改已经是应用了

只是在UI看来没有超过100罢了。以及如果有人去读basevalue也会走到这里来导致其值为Max看起来没有问题

但是只要一应用GE 就会发现没有在扣血，在扣除base超过上限的部分。

可以理解为pre只是用来处理视觉效果的。没有实际修改值



PostGameplayEffectExecute的话就是在GE实施之后实际上修改值的地方。可以使用Set修改base

但是使用PostGameplayEffectExecute需要注意clampduration效果，会导致数值的问题。比如说生命值临时+50.现在是80 上限只能加到100。但是时效一结束会直接移除掉modifier即-50导致角色只有50血。所以对duration的clamp也要注意



所以两个地方其实都要做clamp



### 然后我又发现一些奇奇怪怪的BUG

比如说 如果我+100的duration 然后+X的instant duration就不会消失了

又或者+duration 持续时间内-1instant 会马上加到100  好神秘啊



感觉是这里的问题啊。宏的问题。get宏获取的是current但是set的时候是设置的base

这里可以看出拿的是current设的是base。在duration存在的期间那不就是把duration设置成base了  这里是一点。

还有是post只会在instant里面改base的时候触发



这里的注释写的很清楚了，只会在修改base时调用，不会在duration被调用  这两都是

![d112ad4c-edc8-4725-a590-524cfa4cecd4](./images/d112ad4c-edc8-4725-a590-524cfa4cecd4.png)

```
#define GAMEPLAYATTRIBUTE_VALUE_GETTER(PropertyName) \
    inline float Get##PropertyName() const \
    { \
        return PropertyName.GetCurrentValue(); \
    }

#define GAMEPLAYATTRIBUTE_VALUE_SETTER(PropertyName) \
    inline void Set##PropertyName(float NewVal) \
    { \
        UAbilitySystemComponent* AbilityComp = GetOwningAbilitySystemComponent(); \
        if (ensure(AbilityComp)) \
        { \
            AbilityComp->SetNumericAttributeBase(Get##PropertyName##Attribute(), NewVal); \
        }; \
    }
```

所以结合起来来看。可知。post和pre里面其实就只会处理health 那你额外加的health其实就不在限制范围内了。就我们应该只管base的值有没有超过max

所以这里不能用get来获取，这样会获取到 current

那么数据流向就是这样的 15base开局 + 50dura  此时不会触发post/pre 走到火上去开始扣血 然后再post里设置base为了64 那么此时和dura的buff一加就变成了 64 + 50 = 114 然后显示为100 

另一种情况+100的dura 然后+1instant 此时超过界限设置了base = 100此时 就算dura没了。那base也确实还是100



另一种情况 85  开局 +50dura 因为dura没有参与post/pre此时其实没有限制上限。 所以现在其实是85+50 = 135 然后结束后扣回85   

这一下就说通了都   但是怎么解决呢。不可能不要dura了吧  目前没有想到好的办法。看下后续他设计数值的时候怎么操作吧



### 问了下AI说像lyra这种都是使用的元属性

嗯后面学lyra的时候再看吧。知道现在这些BUG是这样产生的就好

```
终极解决方案”：元属性模式
既然你已经推理出了“不要直接操作 Health”的结论，那么解决这个问题的工业级做法就是 “引入元属性 (Meta Attributes)”。

在成熟的 GAS 项目（如 Lyra）中，Health 属性是不允许被 GE 直接修改的。所有的 GE 都修改 Damage 或 Healing。

第一步：定义元属性
在 .h 中增加两个不复制的属性：

C++
UPROPERTY()
FGameplayAttributeData Damage; // 仅作为伤害载体
ATTRIBUTE_ACCESSORS(UAuraAttributeSet, Damage)

UPROPERTY()
FGameplayAttributeData Healing; 
ATTRIBUTE_ACCESSORS(UAuraAttributeSet, Healing)

第二步：在 PostExecute 中手动“分账”

这是你大展拳脚的地方。在这里，你可以写逻辑让“临时加成”变得有意义。

void UAuraAttributeSet::PostGameplayEffectExecute(const FGameplayEffectModCallbackData& Data)
{
    // 情况 A：处理伤害
    if (Data.EvaluatedData.Attribute == GetDamageAttribute())
    {
        float LocalDamage = GetDamage();
        SetDamage(0.f); // 立即归零，因为它只是个传声筒

        if (LocalDamage > 0.f)
        {
            // 这里你可以决定：是看 CurrentHealth 还是 BaseHealth
            // 关键：为了让 Dura Buff 挡刀，我们看 CurrentValue
            const float CurrentH = GetHealth(); 
            const float BaseH = Health.GetBaseValue();

            // 如果当前总血量（含Buff）够扣
            // 我们允许 BaseValue 变负！(这是 GAS 处理临时血量消耗的秘诀)
            const float NewBase = BaseH - LocalDamage;

            // 使用 SetBaseValue 物理写入，绝不使用 SetHealth 宏
            Health.SetBaseValue(NewBase);
            // 手动同步 Current，此时 Current = NewBase + Modifiers
            Health.SetCurrentValue(NewBase + (GetHealth() - GetHealthAttribute().GetNumericValue(this)));
        }
    }

    // 情况 B：处理治疗（这就解决了你“加不上血”的问题）
    if (Data.EvaluatedData.Attribute == GetHealingAttribute())
    {
        float LocalHealing = GetHealing();
        SetHealing(0.f);

        if (LocalHealing > 0.f)
        {
            float NewBase = Health.GetBaseValue() + LocalHealing;
            float MaxH = GetMaxHealth();

            // 物理限制 Base 不超过 Max，这样无论你有多少 Buff，你的底账永远干净
            NewBase = FMath::Clamp(NewBase, 0.f, MaxH);

            Health.SetBaseValue(NewBase);
        }
    }
}

4. 为什么这个办法解决了你的所有困扰？

1. **Dura Buff 终于能挡刀了**：当你有 15 Base 和 50 Dura 时，受到 30 伤害。Base 变成 -15，但 Current 依然是 `(-15) + 50 = 35`。你活了下来！
2. **不再跳血变 100**：因为治疗（Healing）现在是直接操作 `SetBaseValue` 的，它完全不理会当前有没有 +50 的 Buff。你加了 20 血，Base 就变成 35，Buff 结束后你还是 35。
3. **上限判定变准了**：你只管 BaseValue 有没有超过 100。Buff 提供的额外 50 点是“溢出部分”，它会在 UI 上显示为 135/100（或者你可以在 UI 逻辑里 Clamp 它），但在逻辑底层，你的账本是清爽的。

### 总结

你之前的无语是因为你试图在 **“结算层 (Execute)”** 用 **“表现层 (Current/Set宏)”** 的逻辑去补救。**GAS 的高手从不直接 `SetHealth`。** 他们通过 `Damage` 元属性在 C++ 里手动做减法，这样既保住了 BaseValue 的尊严，也让 Duration Buff 真正成了“救命稻草”。第二步：在 PostExecute 中手动“分账”这是你大展拳脚的地方。在这里，你可以写逻辑让“临时加成”变得有意义。

C++void UAuraAttributeSet::PostGameplayEffectExecute(const FGameplayEffectModCallbackData& Data){ // 情况 A：处理伤害 if (Data.EvaluatedData.Attribute == GetDamageAttribute()) { float LocalDamage = GetDamage(); SetDamage(0.f); if (LocalDamage > 0.f) { const float CurrentH = GetHealth(); // 含 Buff 的总血量 const float BaseH = Health.GetBaseValue(); // 关键：允许 BaseValue 变负！(这是 GAS 处理临时血量消耗的秘诀) const float NewBase = BaseH - LocalDamage; // 使用 SetBaseValue 物理写入，绝不使用 SetHealth 宏 Health.SetBaseValue(NewBase); // 手动同步 Current，此时 Current = NewBase + Modifiers Health.SetCurrentValue(NewBase + (GetHealth() - GetHealthAttribute().GetNumericValue(this))); // 只有当 CurrentValue（含 Buff）都小于 0 时，才判定消除 (Elimination) if (Health.GetCurrentValue() <= 0.f) { /* 执行消除逻辑 */ } } } // 情况 B：处理治疗 if (Data.EvaluatedData.Attribute == GetHealingAttribute()) { float LocalHealing = GetHealing(); SetHealing(0.f); if (LocalHealing > 0.f) { float NewBase = Health.GetBaseValue() + LocalHealing; float MaxH = GetMaxHealth(); // 物理限制 Base 不超过 Max，这样无论你有多少 Buff，你的底账永远干净 NewBase = FMath::Clamp(NewBase, -MaxH, MaxH); // 允许负值，但封顶 Max Health.SetBaseValue(NewBase); Health.SetCurrentValue(NewBase + (GetHealth() - GetHealthAttribute().GetNumericValue(this))); } }

}
4. 为什么这个办法解决了你的所有困扰？Dura Buff 终于能挡刀了： 当你有 15 Base 和 50 Dura 时，受到 30 伤害。Base 变成 -15，但 Current 依然是 (-15) + 50 = 35。你活了下来！不再跳血变 100： 因为治疗（Healing）现在是直接操作 SetBaseValue 的，它完全不理会当前有没有 +50 的 Buff。你加了 20 血，Base 就从 -15 变成 5，Buff 结束后你还是 5。上限判定变准了： 你只管 BaseValue 有没有超过 100。Buff 提供的额外 50 点是“溢出部分”，它会在 UI 上显示为 135/100，但在逻辑底层，你的账本是清爽的。一句话总结： 你之前的痛苦是因为你在 “结算层 (Execute)” 用了 “表现层 (SetHealth 宏)” 的逻辑。通过 Damage 元属性手动操作 SetBaseValue，你就能完美驾驭这套系统。


```











































--
