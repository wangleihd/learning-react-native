# 一句技巧

_本篇文章记录的技巧尽量保持与平时工作的 React Native 相关, 但也有例外。_

## React Native
1. 自定义属性中,必须选其中一种 `shape: PropTypes.oneOf(['round', 'square']).isRequired`
2. 自定义属性中,要么指定具体数字,要么用full `width: PropTypes.oneOfType([PropTypes.number, PropTypes.oneOf(['full'])]).isRequired`
3. 之前判断根据不同平台写 Style 时用`height: Platform.OS === 'ios' ? 200 : 100,` , 今天发现还有另一种写法 `...Platform.select({ ios: { top : 20 }, android : { top : 10 } }),`
4. `componentWillReceiveProps(nextProps)` 在组件接收新的props时触发, 用法: `if (nextProps.project !== this.props.project) { }`

## iOS
1. 要添加或修改 `header` 引用, 可以打开 `pbxproj` 文件, 找到 `HEADER_SEARCH_PATHS` 节点(注意**Debug**,**Release**版), 添加或修改相应引用

## Git
1. 删除**最后一次**缓存记录 `git stash drop stash@{0}`
2. 应用**指定某一次**缓存记录 `git stash apply stash@{3}`
3. **没有 push** 要回滚 `git reset --hard HEAD`
4. **已经 push** 要回滚 `git revert b3c20ba6fb38cc94fe5a8d`

## ES6
1. 用**不定参数** `function foo(a, ...z)`和**默认参数**`function bar(father="Kenny", son="Jerry")` 取代 `arguments` 参数
2. 在 JavaScript 里 null、undefined、0、-0、NaN 和 "" 都为 false
3. 使用 **对象展开语法(Object spread)** 来替换 `Object.assign` 用法, 即: `{ ...state, {name:Kenny} }` 来替换 `Object.assign({}, state, {name:Kenny})`
4. 事件 bind 放在constructor里更高效（bindings once, use forevermore）, 避免使用 Arrow function。如:
<pre><code>constructor(props) {
  super(props);
  this.handleClick = this.handleClick.bind(this);
}
handleClick() { console.log('clicked!'); }
render(){
  return(
  &ltText onPress={this.handleClick}&gtClick Me&lt/Text&gt
  )
}
</code></pre>

## Linux / Mac OS X
1. 清除 DNS 缓存 `sudo killall -HUP mDNSResponder`