# 布局样式基础

* 声明和使用样式
* 布局单位
* 盒子模型
* 定位模式
* css属性

## 声明和使用样式

### 通过StyleSheet声明样式
```
var styles = StyleSheet.create({
  base: {
    width: 38,
    height: 38,
  },
  background: {
    backgroundColor: '#222222',
  },
  active: {
    borderWidth: 2,
    borderColor: '#00ff00',
  }
});
```

### 通过style属性来使用样式

```
// 引用styles
<Text style={styles.base} />
<View style={styles.background} />

// 数组形式引用
<View style={[
			styles.base,
			styles.background]}/>

// 直接使用
<View style={{
         width: 100,
         height:100}}/>
```         

## 布局单位

* 设置高度或者宽度时不用带单位，默认使用 pt 为单位
* 不能使用百分比来设置宽度或高度
* 可通过 Dimensions 模块来获取窗口宽高
* 可通过 PixelRatio 模块来获取像素密度

### Dimensions 和 PixelRatio

我们通过 Dimensions 来获取设备高度和宽度

```
import Dimensions from 'Dimensions';
const {width, height} = Dimensions.get('window');
  <Text>
    宽度： {width}
    {'\n'}
    高度： {height}
  </Text>
```

我们通过 PixelRatio 来获取设备像素密度

```  
import PixelRatio from 'PixelRatio';
const pr = PixelRatio.get();
  <Text>
    window.pixelRatio = {pr}
  </Text>
```

## 盒子模型
跟 css 中的盒子模型一样

## 定位模式
支持 absolute 和 relative 定位

### absolute 定位

```
  <View style={{
			flex: 1,
			height: 100,
        backgroundColor: '#333333'}}>
    <View style={[styles.circle, {
			position: 'absolute',
			top: 50,
			left: 180}]}>
    </View>
  </View>
```

### relative 定位

```
  <View style={{
			flex: 1,
			height: 100,
        backgroundColor: '#333333'}}>
    <View style={[styles.circle, {
			position: 'relative',
			top: 50,
			left: 50,
			marginLeft: 50}]}>
    </View>
  </View>
```

## css 属性支持

*  transform
*  border  style
*  font style
*  shadow
*  background
*  overflow, opacity
