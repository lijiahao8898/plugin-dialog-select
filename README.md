# 自用选择插件 select-plugin

## 插件描述
该插件主要实现的功能是将选择某数据之后返回。

## 插件要实现的功能：（options默认情况下是商品选择）
* 支持单选、多选、sku单选、sku多选、商品选择、用户选择、类目选择、品牌选择、仓库选择、优惠券选择。
* 传入选择框展示的内容type（默认是0,其他【0：商品，1：用户，2：优惠券，3：仓库，4：品牌，5：类目，10：合约-未开发】）
* 支持标题自定义
* 支持全选、单选的判断（单选情况下是否直接关闭弹窗）
* 支持刷新按钮的判断（暂未涉及）
* 支持多个调用并且返回当前点击的指针位置
* 支持多选情况下选择的个数限制 (0 为无限)
* 将请求的借口作为参数传入
* 支持品牌、类目的搜索（需要自己传入品牌、类目的list。并且根据showCateAndBrand判断是否展示）
* 支持下架商品、过期优惠券的隐藏不展示功能。排除无用数据
* 返回一个cb：selectSuccess ( 单选 和 多选 )
* 返回一个cb：selectError ( 数据超出上限会报这个错误 )
* 返回一个cb：ajaxError （ ajax请求报错回调 ）

## 引用：
js:
```
<script type="text/javascript" src="../src/plugin/select-plugin/select-plugin.js"></script>
```
css:
```
<link rel="stylesheet" href="../style/css/selectplugin.css">
```

## 调用：
```
('#plugin').selectPlugin({})
```
## 传参
```
    /**
        * 插件的默认配置项
        * @type {boolean} single: false,               // 判断 selectPlugin 是单选还是多选 默认是多选
        * @type {boolean} isSku: false,                // 判断 selectPlugin 是否支持到sku级别 (主要用于商品)
        * @type {boolean} needSkuGoodsInfo: false      // 判断 selectPlugin 是否在选择sku的时候默认返回商品的名字 默认不返回
        * @type {number}  type: 0                      // 判断 selectPlugin 需要渲染的是什么 (0:商品,1:用户,2:优惠券,3:仓库,4:品牌,5:类目,10:合约)
        * @type {number}  selectLength: 0              // 判断 selectPlugin 多选情况下选择的个数限制 (0 为无限)
        * @type {string}  title                        // 商品选择弹窗的title
        * @type {boolean} isSelectAll                  // 判断是否显示全选按钮
        * @type {boolean} isRefresh                    // 判断是否显示刷新按钮
        * @type {Array}   selectedList                 // 选择的列表
        * @type {string}  ajaxUrl                      // 请求的接口
        * @type {string}  ajaxSkuUrl                   // 请求的SKU接口
        * @type {string}  ajaxType                     // ajax的请求类型默认 post
        * @type {string}  ajaxDataType                 // ajax的请求数据类型默认 json
        * @type {boolean} needFailureInfo              // 是否展示已经失效的东西-垃圾数据 ( 默认情况下是展示 )
        * @type {Array}   categoryList                 // 需要展示的类目列表
        * @type {Array}   brandList                    // 需要展示的品牌列表
        * @type {boolean} showCateAndBrand             // 是否展示类目列表和品牌列表的搜索 ( 默认false )
        * function selectSuccess                       // 成功选择之后的回调 返回选择的数据data,和当前选择弹框的指针
        * function selectError                         // 失败选择之后的回调 返回一条错误信息info
        * function ajaxError                           // 接口请求报错后的回调
        */
 ```
### 需要修改
 1. 支持出商品外的其他数据的选择


> update

2017.6.15
1. 增加了品牌和类目的type类型
2. 将接口更改为参数
ps: 选择类目后一二级类目都会返回.请自行处理

2017.6.12
1. 增加了categoryList的配置项
2. 增加了categoryList的配置项
3. 增加了showCateAndBrand的配置项用于控制categoryList和brandList的展示

2017.5.26
1. 增加了needFailureInfo的配置项

2017.5.18
1. 增加了ajaxType的类型
2. 增加了ajaxDataType的类型
3. 增加接口请求错误后的回调ajaxError
4. 相关优化

> bug

同一个type类型不能同时出现2个或者以上的bug 导致选择的时候多次点击
 
