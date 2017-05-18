# select-plugin

                                    =======================================
                                    =========   自用-弹窗选择插件   =========
                                    =======================================

## 插件描述
该插件主要实现的功能是将选择某数据之后返回。

## 插件要实现的功能：（options默认情况下是商品选择）
* 支持单选、多选、sku单选、sku多选。
* 传入选择框展示的内容type（默认是0,其他0:商品,1:用户,2:优惠券,3:仓库,10:合约）
* 支持标题自定义
* 支持全选、单选的判断（单选情况下是否直接关闭弹窗）
* 支持刷新按钮的判断（暂未涉及）
* 支持多个调用并且返回当前点击的指针位置
* 支持多选情况下选择的个数限制 (0 为无限)
* 返回一个cb：selectSuccess ( 单选 和 多选 )
* 返回一个cb：selectError ( 数据超出上限会报这个错误 )

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
     * @type {number}  type: 0                      // 判断 selectPlugin 需要渲染的是什么 (0:商品,1:用户,2:优惠券,3:仓库,10:合约)
     * @type {number}  selectLength: 0              // 判断 selectPlugin 多选情况下选择的个数限制 (0 为无限)
     * @type {string}  title                        // 商品选择弹窗的title
     * @type {boolean} isSelectAll                  // 判断是否显示全选按钮
     * @type {boolean} isRefresh                    // 判断是否显示刷新按钮
     * @type {Array}   selectedList                 // 选择的列表
     * @type {string}  ajaxType                     // ajax的请求类型默认 post
     * @type {string}  ajaxDataType                 // ajax的请求数据类型默认 json
     * function selectSuccess                       // 成功选择之后的回调
     * function selectError                         // 失败选择之后的回调
     */
 ```
### 需要修改
 1. 支持出商品外的其他数据的选择


> update

1. id 判断选中 增加了item_id 服务端返回的只有item_id   验证拼团
2. 修复有两个dialog同时出现的展示异常
3. 增加优惠券的选择
 
