
![](http://greper.veryreader.com/extends/banner1.png)


# 【d2-crud-plus】面向配置的crud编程
基于d2-admin 的 d2-crud 的扩展,简化d2-crud配置，快速开发crud功能。   

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)

<a href="https://github.com/d2-projects/d2-admin" target="_blank"><img src="https://raw.githubusercontent.com/d2-projects/d2-admin/master/docs/image/d2-admin%402x.png" width="200"></a>

## 帮助文档 
%%%%%%%%%%%%%%%%%%%%%%% 帮助文档 ↓%%%%%%%%%%%%%%%%%%%%%%%%%%%%
> 
>GitHub Pages   
>https://greper.github.io/d2-crud-plus/
>
>码云（国内访问推荐 ）  
>http://greper.gitee.io/d2-crud-plus/   
>
>示例演示   
>http://qiniu.veryreader.com/D2CrudPlusExample/index.html
>
%%%%%%%%%%%%%%%%%%%%%%% 帮助文档 ↑%%%%%%%%%%%%%%%%%%%%%%%%%%%%

## 关系
* `d2-crud` : 官方的一个crud框架，使用起来相对繁琐，且已久不维护
* `d2-crud-x` ：fork`d2-crud`改造而来，威力加强版（修复bug，增强功能）
* `d2-crud-plus`: 辅助`d2-crud-x`或`d2-crud`，让它们使用起来更简单
* `d2-crud-plus-example`: 以`d2-admin`为基础的示例工程，可以单独复制此项目作为你的启动项目
* `d2-crud-plus-extends`: 实用的扩展组件（文件上传组件、地区选择组件、树形选择组件等）


## 面向配置的crud编程
 
### 1. crud.js
开发过程中主要对crud.js进行代码编写  
通常在[示例项目](https://github.com/greper/d2-crud-plus/tree/master/packages/d2-crud-plus-example/src/business/views)
中找一个合适的复制，再根据实际需求修改即可    
也可以根据数据库表以及模版自动生成

更详细的文档：[开发一个crud](http://greper.gitee.io/d2-crud-plus/guide/quickstart.html#开发一个crud)
 
```js
export const crudOptions = (vm)=>{ // vm即this
   return {
     columns: [
       {
         title: '日期',
         key: 'createDate',
         sortable: true, 
         type: 'date', //字段类型为时间选择器datepicker,根据类型可自动生成默认配置
         search: {//查询配置，默认启用查询
           disabled: true //【可选】true禁止查询,默认为false
         },
         form: {//form表单的配置
           disabled: true, //禁止添加输入与修改输入【可选】默认false
         }
       },
       {
         title: '状态',
         key: 'status',
         search: {},//启用查询
         type: 'select', //字段类型为选择框
         form: { //配置添加和编辑，根据form的配置自动生成addTemplate和editTemplate
           rules: [//【可选】添加和修改时的校验规则，不配置则不校验
             { required: true, message: '请选择状态' }
           ]
         },
         dict: { //数据字典配置
           url: '/api/dicts/StatusEnum' //远程获取数据字典
         }
       },
       {
         title: '地区', 
         key: 'province', 
         search: {},//启用查询
         type: 'select', //字段类型为选择框
         form: {
           rules: [{ required: true, message: '请选择地区' }],
           component: { //添加和修改时form表单的组件，支持任何v-model组件
             props: { //配置自定义组件的属性
               filterable: true, //可过滤选择项
               multiple: true, //支持多选
               clearable: true //可清除
             }
           }
         },
         dict: {  //本地数据字典
           data: [
             { value: 'sz', label: '深圳' }, 
             { value: 'gz', label: '广州' }, 
             { value: 'wh', label: '武汉' }, 
             { value: 'sh', label: '上海' }
           ]
         }
       }
     ]
   }
}
``` 

更详细的文档：[快速开始](http://greper.gitee.io/d2-crud-plus/guide/quickstart.html)


### 2. 看效果   

![](https://raw.githubusercontent.com/greper/d2-crud-plus/master/packages/d2-crud-plus/doc/image/list.png)

![](https://raw.githubusercontent.com/greper/d2-crud-plus/master/packages/d2-crud-plus/doc/image/add.png)

![](https://raw.githubusercontent.com/greper/d2-crud-plus/master/packages/d2-crud-plus/doc/image/edit.png)



## 帮助文档 
%%%%%%%%%%%%%%%%%%%%%%% 帮助文档 ↓%%%%%%%%%%%%%%%%%%%%%%%%%%%%
> 
>GitHub Pages   
>https://greper.github.io/d2-crud-plus/
>
>码云（国内访问推荐 ）  
>http://greper.gitee.io/d2-crud-plus/   
>
>示例演示   
>http://qiniu.veryreader.com/D2CrudPlusExample/index.html
>
%%%%%%%%%%%%%%%%%%%%%%% 帮助文档 ↑%%%%%%%%%%%%%%%%%%%%%%%%%%%%

## 联系作者

[欢迎bug反馈，需求建议，技术交流等（请备注d2-crud-plus）](http://greper.gitee.io/d2-crud-plus/guide/contact.html)

![](http://d2p.file.veryreader.com/greper/contact.png)

