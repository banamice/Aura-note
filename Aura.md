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

需要注意 使用增强输入需要添加model "EnhancedInput" 

![82253bb4-fa8e-4a18-8760-6ce6329851f2](./images/82253bb4-fa8e-4a18-8760-6ce6329851f2.png)



增强输入的数据流向大概是： 按键按下 inputlocalplayer接收到->查看其下的context 看将这个输入转换给哪一个iinput action  ->  当ia改变时会通知其绑定的inputCompojnent触发对应的回调



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



## 第一章结束

主要就是配置了一些基础的角色控制 高亮


