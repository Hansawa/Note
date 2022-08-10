[toc]

## display: flex

flexible box，弹性布局，用来为盒状模型提供最大的灵活性

采用 flex 布局的元素，被称作 Flex 容器，简称容器。容器内的元素成为 item，项目

容器中具有主轴，交叉轴的概念，项目根据主轴所设定的值进行排列，根据交叉轴所设定的值进行对齐

介绍：[Flex 布局教程：语法篇 - 阮一峰的网络日志 (ruanyifeng.com)](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

### 容器的属性

#### justify-content

设置每个项目在主轴方向上的排列方式

#### align-item

设置每个项目在交叉轴上的对齐方式

让上面两个属性设置为 center 就会水平垂直居中

#### flex-direction

决定主轴的方向，及项目的排列方向