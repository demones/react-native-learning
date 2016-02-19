# 图片 Image 组件介绍

* Image 组件
* 引用静态图片
* 引入网络图片
* ResizeMode
* 嵌套Text

Image 组件通过source来指定资源，资源可以是本地的资源，也可以是网络上的资源，下面是一个Image 组件使用示例

 ```
  <Image
      style={styles.logo}
      source={{uri: 'http://facebook.github.io/react/img/logo_og.png'}}
  />
  ```

**注意写法**

```
// GOOD
<Image source={require('./my-icon.png')} />

// BAD
var icon = this.props.active ? 'my-icon-active' : 'my-icon-inactive';
<Image source={require('./' + icon + '.png')} />

// GOOD
var icon = this.props.active ? require('./my-icon-active.png') : require('./my-icon-inactive.png');
<Image source={icon} />
```

## 本地引入图片资源

这里需要注意的是，React native 0.14 中引入本地图片资源与之前版本有所不同，详见官方说明
https://facebook.github.io/react-native/docs/images.html

```
<Image source={require('./images/logo.png')}/>
```

## 通过 uri 引入外部链接

```
<Image style={{width: 291, height: 291}}
    source={{uri: 'http://facebook.github.io/react/img/logo_og.png'}}
  />
```

**这里需要注意的是，通过外部引入的链接需要设置其高度和宽度，否则会无法显示，而引入本地图片不需要**

## resizeMode 模式

通过resizeMode 改变图片显示效果，类似css 的背景模式

```
resizeMode enum('cover', 'contain', 'stretch')
```
以下给出例子

```
<View style={{backgroundColor: 'black', marginBottom: 10}}>
  <Image
    source={require('./images/logo.png')}
    style={{
      height: 100,
      resizeMode: 'cover'
    }}
  />
</View>
```

## 在 Image 中嵌套其他元素
不同于html中的Image元素，React Native 中的Image可嵌套其他元素

```
<Image style={{
		flex: 1,
		height: 100,
		justifyContent:'center',
		alignItems: 'center'}}
		source={{uri: ‘…’}}>
       <Text style={{color: 'red'}}>Image Description</Text>
   </Image>
```

例子

```
<Image
  source={require('./images/logo.png')}
  style={{
    height: 100,
    resizeMode: 'cover',
    alignItems: 'center', justifyContent: 'center'
  }}
>
  <Text style={{color: 'red'}}>Hello World</Text>
</Image>
```
