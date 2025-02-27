

# Calculation-Problem

常见的工作计算函数 / 面试函数

## Decorator
```
   Decorator                             装饰器    属性 -> 访问 -> 参数 -> 方法
   |
   ├── class                             类装饰器
   |   └── drag                           └── 拖拽装饰器
   |
   ├── method                            方法装饰器
   │   │                                  │
   │   ├── ParameterRoute                 ├── 参数化路由
   │   │                                  │
   │   └── public                         └── 公共装饰器
   │
   └── types.ts         定义类型
```
<img src="https://raw.githubusercontent.com/Due07/Calculation-Problem/master/image/image-20221103180504481.png" alt="image-20221103180504481" />

```typescript
   import { InitializationAddress, addRouteAddress } from '../Decorator/method/ParameterRoute';
   // 参数化路由
   export default class UserList extends Vue {
      form = {
         size: 10,
         page: 1,
      };

      @InitializationAddress('form')
      mounted() {
         // ....发送请求方法
         this.fetch(this.form);
      }

      @addRouteAddress('type')
      fetch(data: any) {
         // 发送请求
         // this.http(data)....
      }
   }

```


## QuillEditor
```
   // 富文本 + 裁剪
   (quill + vue-quill-editor) + cropper.js

   上传文件方向(不贴代码): 
      1. 调用存储数据库本地 ---> (如果面向用户, 很容易数据库就满了, 崩溃～～～ )
      2. 自行调用aws/oss/qiniu云服务, key什么的有前端存（不安全）
      3. (推荐) 后端存储key 等，前端负责常规获取接口，后端返回云服务的预地址, 进行存储

   更新问题点：
      1. 修复富文本黏贴图片时base64的问题
      2. 修改默认的字体大小 / 配置动态化字体大小

```

## Http
```typescript
   封装axios
      功能点: 节流(拦截重复请求)、配合多语言化请求返回信息、统一管理response、error信息提醒
```

## TemplateRender (模拟模版渲染)
```javascript
   ** 一个简单的模版渲染 **

   缺: 没有ejs渲染的if / forearch / 声明常量 set xx  判断, 后期想到就补上

   类似vue的 {{ }} 当然没有VNode (原因还没看😅)

   VNode: 可以找一下snabbdom 思想, vue也是在这基础上建立的 link: https://github.com/coconilu/Blog/issues/152
   // 类似于eval 把字符串转成代码化之行
   new Function : https://javascript.info/new-function
```

## Transfer (穿梭框)
> **vue-property-decorator + typescript + vue2.6 + elem**
>
> **穿梭框小组件 需求: 列表展示时，自定义化表头**   
>
> |                            设置前                            |                            设置后                            |
> | :----------------------------------------------------------: | :----------------------------------------------------------: |
> | <img src="https://raw.githubusercontent.com/Due07/Calculation-Problem/master/image/image-20220923115231264.png" alt="image-20220923115231264" style="zoom: 50%; display: inline-block" /> | <img src="https://raw.githubusercontent.com/Due07/Calculation-Problem/master/image/image-20220923115654730.png" alt="image-20220923115654730" style="zoom: 60%; display: inline-block" /> |
>
> elem的穿梭框支持render渲染（tsx / jsx）
>
> tips：tableAll (全部表头) 、defaultTable (默认表头)、customTable (已设置的自定义表头) 需要考虑好类型格式
>
> 

## Image-Template（图片组件）
> **Attributes**
>
> - src 							---------->	 string
> - fit 							---------->     fill / contain / cover / none / scale-down
> - alt 							---------->     string
> - referrerPolicy 			---------->     string
> - lazy 						---------->    boolean
>
> **Events**
>
> - load							---------->    加载成功触发
> - error						---------->    加载失败触发
>
> **Slots**
>
> - placeholder				---------->    未加载的占位内容
> - error				      ---------->    加载失败的内容

```typescript
   // vue-property-decorator + vue + typescript + sass
   // IntersectionObserver 兼容性: https://caniuse.com/?search=IntersectionObserver
   // IntersectionObserver (https://developer.mozilla.org/zh-CN/docs/Web/API/IntersectionObserver/IntersectionObserver)

   // 功能点(主): 懒加载(IntersectionObserver) / 失败占位 / 未加载占位 / 预览
   // 兼容性懒加载(低版本) ————> 未
   // 例：
   <ImageComponent
      lazy
      :src=""
      :previewSrcList=""
      :alt=""
      fit="fill"
      :referrerPolicy
      @load=""
      @error=""
   >
   <template #placeholder>.........</template>

   <template #error>.........</template>

   </ImageComponent>

```
## VuePublic（压缩public文件夹中js文件）
```
   业务需求
   需要把一些页面单独放到public文件夹中
   对public文件夹中js文件进行压缩，解决生产环境中代码的暴露
   tips: 打包过程中如果提示download webpack-cli
         可以使用node_modules/ 下的webpack 执行代码块 / 也可下载 npm i webpack-cli@4 -D
```

## Raffle 九宫格抽奖盒子动画
```
   业务需求：
      支持 原生dom 或者 vue 中for渲染出来盒子 抽奖动画
```

## WindowDrag 模拟window文件拖拽
v2 / v3 版本以实现
```
   业务需求：
      实现自定义显示表头
```
<img src="https://raw.githubusercontent.com/Due07/Calculation-Problem/master/image/window-drag.gif" alt="image-20220923115231264" style="zoom: 50%; display: inline-block" />

[![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=Due07&count_private=true&theme=github_dark&show_icons=true)](https://github.com/anuraghazra/github-readme-stats)