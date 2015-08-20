## 概述
```js
{
    "name": "课程展示面板", // 必填
    "path": "class1",       // 必填
    "type": "pc",           // 可选，默认 pc ，其他可选值 h5 | '通用'(pc 和 h5 都可以用)
    "creator": "lqlongli",  // 必填
    "desc": "布局形式是上面一张大图片，下面两张小图片，合集经常使用", // 必填，53 到 60 个汉字
    "proj": "edu",  // 所属项目的英文 key ， edu 为在线教育
    "css": "css/index.css", // 可选，默认 css/index.css ， 如果没有 css ，务必设为 "empty"， 即 "css": "empty"
    "js": "js/index.js",   // 可选，默认 js/index.js ， 如果没有 js ，务必设为 "empty"， 即 "css": "empty"
    "tpl": "tpl/index.html", // 可选，默认 tpl/index.html
    "thumb": "thumb.png",  // 可选，默认 thumb.png    190 x 115
    "jsOptions": ["id"], // 有 js 时必填
    "propertySetting": [
        {
            "key": "partNum",           // 属性 key ，会做为 js 参数传递，比如这里 partNum: 5
            "type": "text",             // 表单类型
            "label": "part标号",        // 表单 label
            "default": 5,               // 默认值
            "tips": "标题标号数字",     // 表单提示
            "validate": "number",       // 验证规则
            "validatetips":"请输入数字" // 验证出错提示
        }
    ]
}
```



## propertySetting 中的 type
propertySetting列表中的每个对象代表组件的一个字段，这个字段的属性值可在运营管理系统编辑页面修改。字段在编辑页面以何种方式呈现取决于type值。如type值是text，则编辑页面会展示一个输入框来编辑该属性值。
 __string:__ 
关键属性type，type值固定是text
 __file:__ 
关键属性type，type值固定是file，提供上传文件的功能
 __select：__ 
关键属性是type、configValue，type固定是select，configValue是一个数组，数组中key是值，value是展示在前台的文本.
配置示例：
```
{
            "key": "background-position",
            "type": "select",
            "label": "背景位置1",
            "configValue":[{"key":"center top","value":"顶部居中"}, {"key":"center","value":"顶部"}]
 }
```
 __color:__ 
关键属性是type，type固定是color
配置示例：
```
{
            "key": "cColor",
            "styleName": "background-color",
            "selector": ".oc-courseList",
            "type": "color",
            "selector":" ",
            "label": "背景颜色"
}
```
 __defaultlist：__ 
关键属性是type，type固定是defaultlist
配置示例：
```
{
            "key": "course_ids",
            "type": "defaultlist",
            "label": "课程ID列表",
            "tips": "课程ID，请输入数字"
}
```


 __特殊属性说明__ 
 __validate：__ 
关键字是validate和validatetips，validate中是写校验器名称，validatetips是校验失败的提示语。
配置示例：


``` 
{
            "key": "course_ids",
            "type": "defaultlist",
            "label": "课程ID列表",
            "tips": "课程ID，请输入数字",
            "validate": "number",
            "validatetips":"请输入数字"
 }
```


注：默认校验器有：


``` 
email 邮箱验证
mobile 手机号码验证
uin qq号或qq群号验证
date 日期验证
uppercase 是否全大写字母
lowercase 是否全小写字母
JSON 是否是JSON串
limit() 值是否在[min, max]区间
not_null 是否非空
number 是否数字
```


> 当前扩展了number校验器，扩展建议统一放在
edu_cms\www\resource\module\validator\validator.plugins.js里面
