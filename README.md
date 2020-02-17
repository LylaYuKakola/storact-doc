## STORACT

使用 'react-hooks API', 类似redux的react状态管理工具

源码及示例: [github](https://github.com/LylaYuKakola/storact)

### 介绍

对比redux，做出了以下修改

1. 使用react-hooks，通过use的方式代替'mapStateToProps'和'mapDispatchToProps'
2. 去掉声明式的action
3. 固化基础的reducer，减少基础操作的定义
4. 参考dva，增加effects的定义
5. 增加dispatch的配置，使其拥有延迟触发、防抖节流、异步挂起的功能
6. 参考dva，去掉"单一数据源"的概念，改为多数据源，并真正实现各个数据源隔离
7. 中间件改成类似koa的洋葱模式，并改成async方法
8. 获

### 示例

```
git clone https://github.com/LylaYuKakola/storact.git
npm intall
npm start
```
/dome/src/

### 开始

```
npm install storact
```

#### step 1

```javascript
import storact from 'storact'

const {
  useDispatch,
  useStoreState,
  Provider,
} = storact({
  initialState, // store的初始状态 - optional
  middlewares, // 中间件集合 - optional
  effects, // effect集合 - optional
  namespace, // 命名空间 - optional
})

export { useDispatch, useStoreState, Provider }
```

#### 参数 initialState —— 初始状态

建议传入一个k-v的Object，作为store的初始状态，如果stroe需要异步初始化，可以不传

#### 参数 middlewares —— 中间件集合

这里中间件改成的编写格式如下

```javascript
({ getState }) => next => async action => {
  // 下一个中间件执行前
  await next(action)
  // 下一个中间件执行之后
},
```
- getState: 获取当前状态的方法
- next: 执行下一个中间件，请注意，这里调用必须加await
- action: 和redux一样


