# 文本 Text 组件

* Text 元素
* Text 元素属性
* Text 嵌套
* Text 样式继承

**注意：和React Web不同的是， 在React Native 中，文本元素必须要用Text 组件包含起来，否则会报错，我们可以使用如下的方式来创建文本**

```
  <Text>some Text</Text>
```

## 文本元素支持的css属性
* color ColorPropType
* fontFamily string
* fontSize number
* fontStyle enum('normal', 'italic')
* fontWeight enum("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
* textShadowOffset {width: number, height: number}
* textShadowRadius number
* textShadowColor ColorPropType
* letterSpacing number
* lineHeight number
* textAlign enum("auto", 'left', 'right', 'center', 'justify')
* textAlignVertical enum("auto", 'top', 'bottom', 'center')
* textDecorationLine enum("none", 'underline', 'line-through', 'underline line-through')
* textDecorationStyle enum("solid", 'double', 'dotted', 'dashed')
* textDecorationColor ColorPropType
* writingDirection enum("auto", 'ltr', 'rtl')

## 文本元素可以嵌套文本元素，内部使用 NSAttributedString

```
<Text style={{fontWeight: 'bold'}}>
  I am bold
  <Text style={{color: 'red'}}>
    and red
  </Text>
 </Text>
```

## 样式继承

不同于web的css标准， React Native中文本元素不能继承上级View的样式，
不过Text 内部可实现局部继承，如上例子中，`and red` 是 `bold` 加 `red`。

## 设置文本长度
文本可以通过 numberOfLines 属性设置文本的行数来限制长度，超出部分用 ... 来显示。

```
<Text numberOfLines={5}>
  <Text>
    文本元素{'\n'}
  </Text>
  <Text>
    {'\n'}I have a problem when updating a bundle - it seems that the classloader is
    not unloaded when stopping the bundle or doing an update.
    This prevents me from correctly updating a solution that consists of 2
    bundles (an API and the Impl).
    See snippet from the logfile:
    //=================================
    Error executing command: Unable to resolve module com.foo.services.server
    [269.1] because it is exposed to package 'com.foo.services.api' from
    com.foo.services.api [268.0] and com.foo.services.api [268.1] via two
  </Text>
</Text>
```
