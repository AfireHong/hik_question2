## MutationObserver

该接口提供了监听DOM树所更改的能力

### 实例方法

#### 1、disconnect()

阻止 MutationObserver 实例继续接收的通知，直到再次调用其observe()方法，该观察者对象包含的回调函数都不会再被调用。

#### 2、observe(element,options)

配置MutationObserver在DOM更改匹配给定选项时，通过其回调函数开始接收通知。

第一个参数传递监听的对象，第二个参数传递配置项。

可监听的选项对象有如下：

- attributeFilter 可选
要监视的特定属性名称的数组。如果未包含此属性，则对所有属性的更改都会触发变动通知。无默认值。

- attributeOldValue  可选
当监视节点的属性改动时，将此属性设为 true 将记录任何有改动的属性的上一个值。有关观察属性更改和值记录的详细信息，详见Monitoring attribute values in MutationObserver。无默认值。

- attributes  可选
设为 true 以观察受监视元素的属性值变更。默认值为 false。

- characterData  可选
设为 true 以监视指定目标节点或子节点树中节点所包含的字符数据的变化。无默认值。

- characterDataOldValue  可选
设为 true 以在文本在受监视节点上发生更改时记录节点文本的先前值。详情及例子，请查看 Monitoring text content changes in MutationObserver。无默认值。

- childList 可选
设为 true 以监视目标节点（如果 subtree 为 true，则包含子孙节点）添加或删除新的子节点。默认值为 false。

- subtree  可选
设为 true 以将监视范围扩展至目标节点整个节点树中的所有节点。MutationObserverInit 的其他值也会作用于此子树下的所有节点，而不仅仅只作用于目标节点。默认值为 false。

#### 3、takeRecords()
从MutationObserver的通知队列中删除所有待处理的通知，并将它们返回到MutationRecord对象的新Array中。

### 基本使用

创建一个实例，构造函数传入一个回调函数，该回调每当被指定的节点或子树以及配置项有Dom变动时会被调用。回调函数拥有两个参数：一个是描述所有被触发改动的 MutationRecord 对象数组，另一个是调用该函数的MutationObserver 对象。

我们可以在该回调函数中监听dom元素的改变