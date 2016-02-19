# ActivityIndicatorIOS 组件 - 指示器
该组件用来在 IOS 中显示加载指示器，即我们常说的 loading

## 例子代码

```JavaScript
'use strict';

import React, {
  Component,
  ActivityIndicatorIOS,
  StyleSheet,
  View,
} from 'react-native';

class ToggleAnimatingActivityIndicator extends Component {

  constructor(props, context) {
    super(props, context);
    this.state = {
      animating: true
    };
  }

  setToggleTimeout() {
    setTimeout(
      () => {
        this.setState({animating: !this.state.animating});
        this.setToggleTimeout();
      },
      1200
    );
  }

  componentDidMount() {
    this.setToggleTimeout();
  }

  render() {
    return (
      <ActivityIndicatorIOS
        animating={this.state.animating}
        style={[styles.centering, {height: 80}]}
        size="large"
      />
    );
  }
}

export default [
  {
    title: 'Default (small, white)',
    render () {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 40}]}
          color="white"
        />
      );
    }
  },
  {
    title: 'Gray',
    render () {
      return (
        <View>
          <ActivityIndicatorIOS
            style={[styles.centering, {height: 40}]}
          />
          <ActivityIndicatorIOS
            style={[styles.centering, {backgroundColor: '#eeeeee', height: 40}]}
          />
        </View>
      );
    }
  },
  {
    title: 'Custom colors',
    render () {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS color="#0000ff"/>
          <ActivityIndicatorIOS color="#aa00aa"/>
          <ActivityIndicatorIOS color="#aa3300"/>
          <ActivityIndicatorIOS color="#00aa00"/>
        </View>
      );
    }
  },
  {
    title: 'Large',
    render () {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 80}]}
          color="white"
          size="large"
        />
      );
    }
  },
  {
    title: 'Large, custom colors',
    render () {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS
            size="large"
            color="#0000ff"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa00aa"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa3300"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#00aa00"
          />
        </View>
      );
    }
  },
  {
    title: 'Start/stop',
    render () {
      return <ToggleAnimatingActivityIndicator />;
    }
  },
];

const styles = StyleSheet.create({
  centering: {
    alignItems: 'center',
    justifyContent: 'center',
  },
  gray: {
    backgroundColor: '#cccccc',
  },
  horizontal: {
    flexDirection: 'row',
    justifyContent: 'space-around',
  },
});

```

调用

``` JavaScript
{
  ActivityIndicatorIOSExample.map((item, index) => {
    return (
      <View key={index} style={{flex: 1, marginBottom: 10}}>
        <Text>{item.title}</Text>
        <Text>{item.description}</Text>
        <View style={{height: 30}}>
          {item.render()}
        </View>
      </View>
    );
  })
}
```

## 中英文官方说明

http://reactnative.cn/docs/activityindicatorios.html#content

https://facebook.github.io/react-native/docs/activityindicatorios.html#content
