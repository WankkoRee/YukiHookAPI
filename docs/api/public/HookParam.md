## HookParam [class]

```kotlin
class HookParam(private​ ​val​ ​createrInstance​:​ ​YukiHookCreater​, private val wrapper: HookParamWrapper)
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> Hook 方法、构造类的目标对象实现类。

### args [field]

```kotlin
val args: Array<Any?>
```

<b>变更记录</b>

在 `v1.0` 添加

<b>功能描述</b>

> 获取当前 Hook 对象 `member` 或 `constructor` 的参数对象数组。

### firstArgs [field]

```kotlin
val firstArgs: Any?
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 对象 `member` 或 `constructor` 的参数对象数组第一位。

### lastArgs [field]

```kotlin
val lastArgs: Any?
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 对象 `member` 或 `constructor` 的参数对象数组最后一位。

### instance [field]

```kotlin
val instance: Any
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 实例的对象。

!> 如果你当前 Hook 的对象是一个静态，那么它将不存在实例的对象。

### instanceClass [field]

```kotlin
val instanceClass: Class<*>
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 实例的类对象。

### method [field]

```kotlin
val method: Method
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 对象的方法。

### constructor [field]

```kotlin
val constructor: Constructor
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 对象的构造方法。

### result [field]

```kotlin
var result: Any?
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取、设置当前 Hook 对象的 `method` 或 `constructor` 的返回值。

### firstArgs [method]

```kotlin
inline fun <reified T> firstArgs(): T?
```

<b>变更记录</b>

`v1.0.66` `新增`

<b>功能描述</b>

> 获取当前 Hook 对象 [method] or [constructor] 的参数对象数组第一位 `T`。

### lastArgs [method]

```kotlin
inline fun <reified T> lastArgs(): T?
```

<b>变更记录</b>

`v1.0.66` `新增`

<b>功能描述</b>

> 获取当前 Hook 对象 [method] or [constructor] 的参数对象数组最后一位 `T`。

### instance [method]

```kotlin
inline fun <reified T> instance(): T
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 实例的对象 `T`。

<b>功能示例</b>

你可以通过 `instance` 方法轻松使用泛型 `cast` 为目标对象的类型。

> 示例如下

```kotlin
instance<Activity>().finish()
```

### args [method]

```kotlin
fun args(index: Int): ArgsModifyer
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 获取当前 Hook 对象的 `method` 或 `constructor` 的参数实例化对象类。

<b>功能示例</b>

你可以通过 `args` 方法修改当前 Hook 实例的方法、构造方法的参数内容。

`index` 的默认值为 `0`，如果只有一位 `param` 参数，你可以不写。

你可以直接使用 `set` 方法设置 `param` 为你的目标实例，接受 `Any` 类型。

!> 请确保 `param` 类型为你的目标实例类型。

> 示例如下

```kotlin
args().set("modify the value")
```

你还可以使用 `setNull` 方法设置 `param` 为空。

> 示例如下

```kotlin
args(index = 1).setNull()
```

你还可以使用 `setTrue` 方法设置 `param` 为 `true`。

!> 请确保 `param` 类型为 `Boolean`。

> 示例如下

```kotlin
args(index = 2).setTrue()
```

你还可以使用 `setFalse` 方法设置 `param` 为 `false`。

!> 请确保 `param` 类型为 `Boolean`。

> 示例如下

```kotlin
args(index = 3).setFalse()
```

### invokeOriginal [method]

```kotlin
fun <T> Member.invokeOriginal(vararg args: Any?): Any?
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 执行原始 `Member`。

<b>功能实例</b>

此方法可以 `invoke` 原始未经 Hook 的 `Member` 对象，取决于原始 `Member` 的参数和类型。

> 示例如下

```kotlin
member.invokeOriginal("test value")
```

### resultTrue [method]

```kotlin
fun resultTrue()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置当前 Hook 对象方法的 `result` 返回值为 `true`。

!> 请确保 `result` 类型为 `Boolean`。

### resultFalse [method]

```kotlin
fun resultFalse()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置当前 Hook 对象方法的 `result` 返回值为 `false`。

!> 请确保 `result` 类型为 `Boolean`。

### resultNull [method]

```kotlin
fun resultNull()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

!> 此方法将强制设置 Hook 对象方法的 `result` 为 `null`。

### ArgsModifyer [class]

```kotlin
inner class ArgsModifyer(private val index: Int)
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 对方法参数的修改进行实例化类。

#### cast [method]

```kotlin
fun <T> cast(): T?
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`of`~~ 为 `cast`

<b>功能描述</b>

> 得到方法参数的实例对象 `T`。

#### byte [method]

```kotlin
fun byte(): Byte?
```

<b>变更记录</b>

`v1.0.68` `新增`

<b>功能描述</b>

> 得到方法参数的实例对象 Byte。

#### int [method]

```kotlin
fun int(): Int
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofInt`~~ 为 `int`

<b>功能描述</b>

> 得到方法参数的实例对象 Int。

#### long [method]

```kotlin
fun long(): Long
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofLong`~~ 为 `long`

<b>功能描述</b>

> 得到方法参数的实例对象 Long。

#### short [method]

```kotlin
fun short(): Short
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofShort`~~ 为 `short`

<b>功能描述</b>

> 得到方法参数的实例对象 Short。

#### double [method]

```kotlin
fun double(): Double
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofDouble`~~ 为 `double`

<b>功能描述</b>

> 得到方法参数的实例对象 Double。

#### float [method]

```kotlin
fun float(): Float
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofFloat`~~ 为 `float`

<b>功能描述</b>

> 得到方法参数的实例对象 Float。

#### string [method]

```kotlin
fun string(): String
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofString`~~ 为 `string`

<b>功能描述</b>

> 得到方法参数的实例对象 String。

#### char [method]

```kotlin
fun char(): Char
```

<b>变更记录</b>

`v1.0.68` `新增`

<b>功能描述</b>

> 得到方法参数的实例对象 Char。

#### boolean [method]

```kotlin
fun boolean(): Boolean
```

<b>变更记录</b>

`v1.0.66` `新增`

`v1.0.68` `修改`

修改 ~~`ofBoolean`~~ 为 `boolean`

<b>功能描述</b>

> 得到方法参数的实例对象 Boolean。

#### array [method]

```kotlin
inline fun <reified T> array(): Array<T>
```

<b>变更记录</b>

`v1.0.68` `新增`

<b>功能描述</b>

> 得到方法参数的实例对象 Array。

#### list [method]
```kotlin
inline fun <reified T> list(): List<T>
```

<b>变更记录</b>

`v1.0.68` `新增`

<b>功能描述</b>

> 得到方法参数的实例对象 List。

#### set [method]

```kotlin
fun <T> set(any: T?)
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置方法参数的实例对象。

#### setNull [method]

```kotlin
fun setNull()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置方法参数的实例对象为 `null`。

#### setTrue [method]

```kotlin
fun setTrue()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置方法参数的实例对象为 `true`。

!> 请确保目标对象的类型是 `Boolean`。

#### setFalse [method]

```kotlin
fun setFalse()
```

<b>变更记录</b>

`v1.0` `添加`

<b>功能描述</b>

> 设置方法参数的实例对象为 `false`。

!> 请确保目标对象的类型是 `Boolean`。