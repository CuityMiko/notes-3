React-Bootstrap官网：[react-bootstrap.github.io](http://react-bootstrap.github.io/)

---

#一，简介

React-Bootstrap 是一个基于React重构的可复用的前端框架。

#二，开始

请使用bower下载Bootstrap CSS到你的项目里，React-Bootstrap样式基于Bootstrap；

按照下面的方式使用React-Bootstrap组件

### 2.1 CommonJS

```sh 
$ npm install react react-bootstrap

var Alert = require('react-bootstrap/lib/Alert');
// or
var Alert = require('react-bootstrap').Alert;
```

### 2.2 ES6

```sh 
$ npm install react react-bootstrap

import Button from 'react-bootstrap/lib/Button';
// or
import { Button } from 'react-bootstrap';
```

### 2.3 AMD

```sh 
$ bower install react react-bootstrap

define(['react-bootstrap'], function(ReactBootstrap) { var Alert = ReactBootstrap.Alert; ... });
```

### 2.4 Browser globals
```sh 
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/<react-version>/react.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/<react-version>/react-dom.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react-bootstrap/<version>/react-bootstrap.min.js"></script>
<script>
  var Alert = ReactBootstrap.Alert;
</script>
```
---

# 三，常用组件

### 3.1 Buttons
- Options    
使用现有的button style types能够快速的创建一个拥有样式的按钮组件，改变它的样式可以直接修改 `bsStyle` 属性     

```sh 
<ButtonToolbar>
    {/* Standard button */}
    <Button>Default</Button>

    {/* Provides extra visual weight and identifies the primary action in a set of buttons */}
    <Button bsStyle="primary">Primary</Button>

    {/* Indicates a successful or positive action */}
    <Button bsStyle="success">Success</Button>
</ButtonToolbar>
<ButtonGroup>
    {/* Contextual button for informational alert messages */}
    <Button bsStyle="info">Info</Button>

    {/* Indicates caution should be taken with this action */}
    <Button bsStyle="warning">Warning</Button>

    {/* Indicates a dangerous or potentially negative action */}
    <Button bsStyle="danger">Danger</Button>

    {/* Deemphasize a button by making it look like a link while maintaining button behavior */}
    <Button bsStyle="link">Link</Button>
  </ButtonGroup>
```    
> `ButtonToolbar` 组件中包含的任意按钮组，相互之间会产生空格元素将其间隔开； `ButtonGroup` 包含的按钮组则不会。     

- Sizes    
想控制按钮的大小？使用 `bsSize="large"`, `bsSize="small"`, or `bsSize="xsmall"` 属性     
```sh
<Button bsSize="large">Small button</Button>
<Button bsSize="small">Small button</Button>
<Button bsSize="xsmall">Extra small button</Button>
```  
- Active state       
设置按钮活动状态很简单，请设置组件的 `active` 属性    
```sh
<Button bsSize="large" active>Button</Button>
```     
- Disabled state         
设置按钮不可用，可设置 `disabled` 属性      
```sh
<Button bsSize="large" disabled>Button</Button>
```       

- Button tags         
当给Button添加 `href` 属性时，按钮渲染到HTML DOM元素上时，会生成 `<a />` 标签，否则生成  `<button />` 标签        



