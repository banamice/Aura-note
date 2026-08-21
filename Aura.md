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
   
   
   ```

```

#define ATTRIBUTE_ACCESSORS(ClassName, PropertyName) \
 *    GAMEPLAYATTRIBUTE_PROPERTY_GETTER(ClassName, PropertyName) \
 *    GAMEPLAYATTRIBUTE_VALUE_GETTER(PropertyName) \
 *    GAMEPLAYATTRIBUTE_VALUE_SETTER(PropertyName) \
 *    GAMEPLAYATTRIBUTE_VALUE_INITTER(PropertyName)

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

















































































































































# 知识点补充

## 什么时候需要使用UPROPERTY修饰指针

背景： UE对于UObject采用自己的一套垃圾回收机制 GC 。 在每一个object对象创建时 ，UE都会将其加入一个全局管理对象数组。每隔一段时间UE都会扫描这数组判断哪些内容应该被回收 ，哪些内容依旧存货。
回收依据：GC 通过UPROPERTY引用链去判断每一个对象。如果能够找到那么就认为存活，如果找不到则认为该回收。这里有一个很重要的点就是 其**不是根据引用计数来判断是否回收的** 这和C++的智能指针是两套方式  。

 如果我们使用裸指针或者智能指针修饰。那么C++知道这个对象还在用 。但是UE不知道，UE只要无法通过UPROPERTY找到这个对象那么就会将其释放导致野指针



回到问题：我们什么时候需要使用UPROPERTY修饰指针 ？

 一句话来说就是：**如果该对象需要在离开作用域后跨帧存活。那么他就需要被UPROPERTY修饰**

         详细来说就是：GC的回收机制只有在游戏线程空闲的时候。可以理解为每一帧的中间时间才会激活。局部变量一定会在该函数中被使用完是不需要修饰的。

```

void AMyActor::SetupTimer()
{
    UMyObject* TempObj = NewObject<UMyObject>(this);
    // ⚠️ 把 TempObj 传给了一个延迟回调
    // 函数结束后，没有 UPROPERTY 持有 TempObj
    // 下一次 GC 扫描时，TempObj 指向的对象就会被回收！
    GetWorldTimerManager().SetTimer(TimerHandle, [TempObj]()
    {
        TempObj->DoSomething(); // 💥 可能已经是野指针
    }, 1.0f, false);

}                

```

比如说在这段代码里。 TempObj被lamda传入了。那么如果不使用UPROPERTY修饰下一次的时候就是野指针了  即使使用了shared_ptr 其也有可能会被GC回收的。标准做法时将其提升为成员变量并修饰



```

UPROPERTY()
TArray<UMyObject*> Objects;

void AMyActor::AddObject()
{
    UMyObject* NewObj = NewObject<UMyObject>(this);
    Objects.Add(NewObj); // ✅ 加入后立即受 GC 保护
}

void AMyActor::RemoveObject(int32 Index)
{
    Objects.RemoveAt(Index); // ✅ 移除后 GC 不再保护，可被回收
}

```

这一段代码演示了UE提供的TArray TMap之类的容器是如何保护其成员变量的  即当容器被标识UPROPERTY之后每次扫描时其内容也会被标识为存活    当然只有UE提供的容器有这种效果

## 不同的asc的复制模式

![9a7feeea-dd83-40f8-b74a-aa0de5f7cc31](./images/9a7feeea-dd83-40f8-b74a-aa0de5f7cc31.png)

## 游戏的单人多人必须在一开始就设计好   多人可以在单人情景游玩，但是单人没法多人游玩

## AcknowledgePossession 和OnRep_Controller

和OnRep_controlller类似都可以标记controller更改 但是这个是包括了处理完成了一系列前置工作

```

在客户端的网络流程中，执行顺序通常是：

Controller 变量同步。
触发 OnRep_Controller。
引擎内部执行 Super::AcknowledgePossession 逻辑（包括更新控制旋转、同步本地组件状态等）。
执行你重写的 AcknowledgePossession 逻辑。
如果你在 OnRep_Controller 中初始化逻辑，可能会遇到“变量虽然有了，但状态还没对齐”的情况（例如控制旋转没生效，或者某些依赖于 Controller 的 Subsystem 还没准备好  



```

并且onrep在监听服务器上不会被执行 。使用AcknowledgePossession的话无论在哪里都会执行，这样可以避免判断是否是客户端还是服务器



```

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
```
`CreateDefaultSubobject` 是 `UObject` 的一个成员函数。当你直接调用它而不指定父对象时，它会**自动将当前对象（即 `this`，你的 PlayerState 实例）设为新创建对象的 Outer**。
 
#### 运行时 (NewObject)
如果你在运行时手动创建对象：
```cpp
// 显式指定 Outer 为 this
UMyObject* Obj = NewObject<UMyObject>(this, UMyObject::StaticClass());
```
第一个参数就是 `Outer`。
 
### 3. Outer 的三大作用
 
#### A. 内存管理与垃圾回收 (GC)
UE 的垃圾回收器会遍历对象图。如果一个对象没有被标记为 `UPROPERTY` 引用，但它有一个合法的 Outer，并且它的 Outer 正在被引用或处于活跃状态，这有助于 GC 理解对象之间的生命周期依赖关系。通常，如果 Outer 被销毁，其所属的 Subobjects 也会被标记为待销毁。
 
#### B. 路径与寻址 (Object Path)
UE 中的每个对象都有一个唯一的路径，格式类似于：
`/Game/Maps/MyLevel.MyLevel:PersistentLevel.MyPlayerState.AttributeSet`
这个路径就是通过不断回溯 `GetOuter()` 直到根部（通常是 Package）构建出来的。
 
#### C. 获取环境上下文 (World Context)
这是最实用的功能。很多 `UObject` 本身并没有 `GetWorld()` 的能力，但它们可以通过 Outer 来“借”一个 World。
例如，`UAttributeSet` 内部并没有保存 World 指针，但当你调用 `GetWorld()` 时，它会调用：
```cpp
UWorld* UObject::GetWorld() const {
    if (Outer) return Outer->GetWorld(); // 递归向上找，直到找到 Actor 或 Level
    return nullptr;
}
```
 
### 4. 回到 GAS 的例子
在你的代码里，`AbilitySystemComponent` 和 `AttributeSet` 的 **Outer 都是同一个 PlayerState**。
 
当 `AbilitySystemComponent` 初始化时，它执行了类似这样的逻辑：
1.  **“谁是我的 Outer？”** -> 得到 `PlayerState`。
2.  **“我的 Outer 还有哪些其他的子对象（Subobjects）？”**
3.  通过反射遍历 `PlayerState` 下属的所有对象，发现：“嘿，这儿有一个 `UAuraAttributeSet` 类型的对象，它的 Outer 也是 PlayerState！”
4.  **“把它加入我的管理列表。”**
 
**总结：**
`Outer` 就像是对象的“户口本”，它定义了你属于谁。正是因为它们都在同一个“户口本”（PlayerState）下，ASC 才能轻松地在同一个家里找到 AttributeSet。
CreateDefaultSubobject 是 UObject 的一个成员函数。当你直接调用它而不指定父对象时，它会自动将当前对象（即 this，你的 PlayerState 实例）设为新创建对象的 Outer。

运行时 (NewObject)
如果你在运行时手动创建对象：

C++
// 显式指定 Outer 为 this
UMyObject* Obj = NewObject<UMyObject>(this, UMyObject::StaticClass());
第一个参数就是 Outer。

3. Outer 的三大作用
A. 内存管理与垃圾回收 (GC)
UE 的垃圾回收器会遍历对象图。如果一个对象没有被标记为 UPROPERTY 引用，但它有一个合法的 Outer，并且它的 Outer 正在被引用或处于活跃状态，这有助于 GC 理解对象之间的生命周期依赖关系。通常，如果 Outer 被销毁，其所属的 Subobjects（子对象）也会被标记为待消除（Elimination）。

B. 获取环境上下文 (World Context)
这是最实用的功能。很多 UObject 本身并没有直接存储 World 指针，但它们可以通过 Outer 来“借”一个 World。 例如，当你对一个 UObject 调用 GetWorld() 时，它的默认逻辑是：

C++
UWorld* UObject::GetWorld() const {
    if (Outer) return Outer->GetWorld(); // 递归向上找，直到找到 Actor 或 Level
    return nullptr;
}
这使得 AttributeSet 即使不是 Actor，也能通过 Outer（PlayerState）访问到当前的关卡世界。

C. 系统发现 (Discovery)
回到你之前的疑惑：ASC 怎么知道 AttributeSet 在哪里？ 因为它们共享同一个 Outer。ASC 内部会调用 GetOuter() 拿到 PlayerState，然后搜索 PlayerState 旗下所有的子对象。如果发现某个子对象的 Outer 是这个 PlayerState 且类型匹配，它们就被关联起来了。

4. 总结
Outer 就像是对象的“户口本”，它定义了你属于谁。正是因为 AttributeSet 的 Outer 被自动设为了 PlayerState，它才会被纳入该 Actor 的生命周期和系统管理之中。
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
```
 
#### B. 创建对象
像 `NewObject` 这样的工厂函数需要知道你想创建什么类型：
```cpp
// NewObject 的默认参数通常就是 T::StaticClass()
UAttributeSet* NewSet = NewObject<UAttributeSet>(Outer, UAttributeSet::StaticClass());
```
 
#### C. 在蓝图中限制类型
当你定义一个 `TSubclassOf` 变量时，底层其实就是在存储 `UClass*`，而 `StaticClass()` 常用于初始化或对比这些变量：
```cpp
UPROPERTY(EditAnywhere)
TSubclassOf<UAttributeSet> AttributeClass;
 
// 在代码中赋值
AttributeClass = UAuraAttributeSet::StaticClass();
```
 
### 5. 它是怎么生成的？
当你编译项目时，**Unreal Header Tool (UHT)** 会扫描你的头文件。如果你写了 `GENERATED_BODY()`，它会在对应的 `.generated.h` 和 `.gen.cpp` 文件中生成类似这样的代码（简化版）：
 
```cpp
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
```
这种单例模式确保了全局范围内，每个类对应的 `UClass` 只有一个，从而实现高效的运行时类型识别（RTTI）。
B. 创建对象
像 NewObject 这样的工厂函数需要知道你想创建什么“模版”：

C++
// 创建一个 UAttributeSet 类型的对象
// 第二个参数其实就是 UClass* 类型
UAttributeSet* NewSet = NewObject<UAttributeSet>(Outer, UAttributeSet::StaticClass());
C. 在蓝图中限制类型选择
当你定义一个 TSubclassOf<T> 变量时，它底层存储的就是 UClass*。你可以用 StaticClass() 给它赋值：

C++
UPROPERTY(EditAnywhere)
TSubclassOf<UAttributeSet> AttributeClass;
 
// 在代码中初始化为特定的类
AttributeClass = UAuraAttributeSet::StaticClass();
5. 它是怎么生成的？
当你编译项目时，Unreal Header Tool (UHT) 会扫描你的头文件。如果你写了 GENERATED_BODY()，它会在对应的 .gen.cpp 文件中生成一段代码。这段代码会确保在引擎启动阶段（早于 BeginPlay），这个 UClass 单例就被创建并注册到全局类型数据库中。

总结： StaticClass() 是你访问 Unreal 反射系统的门票，让你能在运行时像操作数据一样操作“类类型”。
```

## UE的反射系统与UClass*



```
是的，你的理解非常准确。TSubclassOf<T> 在本质上就是一个经过类型安全包装的 UClass* 指针，它指向的就是你所说的元对象（Meta-Object）。

我们可以从以下几个维度来深度理解它：

1. 它确实指向元对象
在 Unreal 中，UClass 实例就是描述类信息的元对象。

UClass* 指向的是“类本身”。
TSubclassOf<AActor> 指向的也是“类本身”，但它在编译器层面加了一个约束：这个类必须是 AActor 或其派生类。
2. 为什么不直接用 UClass*？
如果你在代码里写：

C++
UPROPERTY(EditAnywhere)
UClass* ClassToSpawn;
在编辑器里，下拉列表会显示引擎中所有的类（成千上万个），包括光源、材质、声音等，这会导致数据填写的混乱和崩溃风险。

如果你使用：

C++
UPROPERTY(EditAnywhere)
TSubclassOf<ACharacter> CharacterClass;
编辑器过滤器：下拉列表会自动过滤，只显示 ACharacter 及其子类（如 BP_PlayerCharacter）。这就是你提到的“元对象继承于指定的父类”。

3. 类型安全与编译期检查
TSubclassOf 在 C++ 层面提供了保护。它利用模板在编译时进行检查：

C++
TSubclassOf<UAttributeSet> AttrClass;
 
// 正确：UAuraAttributeSet 继承自 UAttributeSet
AttrClass = UAuraAttributeSet::StaticClass(); 
 
// 编译报错：AActor 并没有继承自 UAttributeSet
// AttrClass = AActor::StaticClass();
4. 它与实例的关系 (关键区别)
这是最容易搞混的地方，请记住这个公式：

TSubclassOf<T> = “图纸”（它是元对象，描述了如何制造一个对象，但它不是对象本身）。
T* (如 ACharacter*) = “实物”（它是已经根据图纸制造出来的、存在于世界中的个体）。
在你的 PlayerState 例子中：

你实例化 UAuraAttributeSet 是为了得到一个实物来存储血量数据。
而如果你想在某个地方设置“我们要生成哪种类型的技能特效”，你会用 TSubclassOf<ANiagaraActor> 来存储那张图纸。
5. 运行时转换
虽然它包装了元对象，但你随时可以把它当做普通 UClass* 使用，比如配合 SpawnActor：

C++
UPROPERTY(EditAnywhere)
TSubclassOf<AActor> ClassToSpawn;
 
// ... 在某个函数里 ...
// 引擎会根据 ClassToSpawn 指向的元对象（图纸），在世界上生成一个实物（实例）
AActor* NewActor = GetWorld()->SpawnActor<AActor>(ClassToSpawn);

```

## getClass 和 xx::StaticClass区别



```
UAttributeSet::StaticClass()：静态调用。意思是：“我要获取代表 UAttributeSet 这个类型的元数据。”（不需要具体对象也能调用）。MyAttributeInstance->GetClass()：实例调用。意思是：“我要看 MyAttributeInstance 这个具体的活对象到底是什么类型的。”这两个是不是获取的都是uclass只不过一个是静态调用 一个是从实际的类对象调用
是的，你的理解完全正确。它们最终指向的都是同一个 UClass 元对象。

我们可以从以下两个层面来拆解它们的相同点与细微差别：

1. 结果的同一性
在内存中，每一个类（无论是在 C++ 定义的还是在蓝图中创建的）都只有一个唯一的 UClass 实例。

假设你有一个 C++ 类 UAuraAttributeSet：

调用 UAuraAttributeSet::StaticClass() 返回的是指针 A。
如果你有一个 UAuraAttributeSet 的实例对象 MyInstance，调用 MyInstance->GetClass() 返回的也是指针 A。
此时，(UAuraAttributeSet::StaticClass() == MyInstance->GetClass()) 的结果为 True。

2. 核心区别：编译时确切性 vs 运行时多态性
这是它们在开发中最关键的区别：

StaticClass() —— “我知道我要什么类型”
它是硬编码的。你在写代码时就已经明确知道你要引用哪个特定的类元数据。

用途：用于类型转换（Cast）、类型判定（IsA）、或者指定工厂函数（NewObject）要生成的模板。
局限性：它无法感知子类。如果你对父类调用 StaticClass()，你永远只能拿到父类的元数据。
GetClass() —— “我要看你实际上是什么”
它是动态的。它支持 C++ 的多态性。

用途：当你拿到一个父类指针（比如 UAttributeSet*），但你想知道它在运行时的真实身份时使用。
威力所在：如果你的 UAuraAttributeSet 被玩家在蓝图中继承并改名为 BP_AuraAttributeSet_C：
UAuraAttributeSet::StaticClass() 依然返回 C++ 父类的元数据。
MyInstance->GetClass() 则会返回那个蓝图子类的元数据。
3. 类比理解
StaticClass() 像是“按名索骥”：你翻开《百科全书》的“猫科”这一页，查看关于猫的定义。
GetClass() 像是“实地考察”：你面前走过来一只动物，你检查它脖子上的挂牌，看它到底是“波斯猫”还是“老虎”。
4. 在 GAS 开发中的实际应用
在你的代码语境下，这种区别非常重要：

C++
// 场景 A：创建对象
// 你明确知道要创建一个 UAuraAttributeSet 类型的实物
AttributeSet = CreateDefaultSubobject<UAuraAttributeSet>(TEXT("AttributeSet"));
 
// 场景 B：处理 GameplayEffect 改变
void UMySet::PostGameplayEffectExecute(const FGameplayEffectModCallbackData& Data)
{
    // Data.Target 是 ASC
    // 我们不知道这个 ASC 是属于什么类的实例（可能是 PlayerState 的，也可能是某个小怪的）
    UClass* ActualClass = Data.Target->GetClass(); 
    
    // 如果我们想判断它是不是某种特殊的 ASC
    if (ActualClass->IsChildOf(UMySpecialAbilitySystemComponent::StaticClass())) 
    {
        // 逻辑处理
    }
}

```
