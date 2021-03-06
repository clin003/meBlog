# Swift语法全面解析



### Swift介绍

Swift 是一门开发 iOS, macOS, watchOS 和 tvOS 应用的新语言。
swift 是一种安全，快速和互动的编程语言。
swift 支持代码预览（playgrounds），这个特性可以允许程序员在不编译和运行应用程序的前提下运行 Swift 代码并实时查看结果。

Swift 通过采用现代编程模式来避免大量常见编程错误：

*    变量始终在使用前初始化。
*    检查数组索引超出范围的错误。
*    检查整数是否溢出。
*    可选值确保明确处理 nil 值。
*    内存被自动管理。
*    错误处理允许从意外故障控制恢复。

###  基础部分
####    常量和变量

声明常量和变量， 常量和变量必须在使用前声明，使用 let 来声明常量，使用 var 来声明变量。
示例：
```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0

// 类型注解
var welcomeMessage: String
```

####    注释

单行注释双正斜杠（//）， 多行注释（/* 多行的 */）。Swift 的多行注释可以嵌套在其它的多行注释之中。
示例：
```swift
// 这是一个注释

/* 这也是一个注释，
但是是多行的 */

/* 这是第一个多行注释的开头
/* 这是第二个被嵌套的多行注释 */
这是第一个多行注释的结尾 */
```
####    分号

Swift 并不强制要求你在每条语句的结尾处使用分号（;）。
同一行内写多条独立的语句必须用分号分隔。
```swift
let cat = "🐱"; print(cat)
// 输出“🐱”
```

####    标识符

标识符就是给变量、常量、方法、函数、枚举、结构体、类、协议等指定的名字。构成标识符的字母均有一定的规范，Swift语言中标识符的命名规则如下：

*    区分大小写，Myname与myname是两个不同的标识符；

*    标识符首字符可以以下划线（_）或者字母开始，但不能是数字；

*    标识符中其他字符可以是下划线（_）、字母或数字。

例如： userName、User_Name、_sys_val、身高等为合法的标识符，而2mail、room#和class为非法的标识符。

注意:Swift中的字母采用的是Unicode编码。Unicode叫做统一编码制，它包含了亚洲文字编码，如中文、日文、韩文等字符，甚至是我们在聊天工具中使用的表情符号

如果一定要使用关键字作为标识符，可以在关键字前后添加重音符号（`），例如：
```swift
let `class` = "xiaobai"
```
####    关键字

关键字是类似于标识符的保留字符序列，除非用重音符号（`）将其括起来，否则不能用作标识符。关键字是对编译器具有特殊意义的预定义保留标识符。常见的关键字有以下4种。
**与声明有关的关键字**

    class 	deinit 	enum 	extension
    func 	import 	init 	internal
    let 	operator 	private 	protocol
    public 	static 	struct 	subscript
    typealias 	var 

**与语句有关的关键字**

    break 	case 	continue 	default
    do 	else 	fallthrough 	for
    if 	in 	return 	switch
    where 	while 		

**表达式和类型关键字**

    as 	dynamicType 	false 	is
    nil 	self 	Self 	super
    true 	_COLUMN_ 	_FILE_ 	_FUNCTION_
    _LINE_ 		

**在特定上下文中使用的关键字**

    associativity 	convenience 	dynamic 	didSet
    final 	get 	infix 	inout
    lazy 	left 	mutating 	none
    nonmutating 	optional 	override 	postfix
    precedence 	prefix 	Protocol 	required
    right 	set 	Type 	unowned
    weak 	willSet 		

####    Swift 空格

Swift对空格的使用有一定的要求。
在Swift中，运算符不能直接跟在变量或常量的后面。例如下面的代码会报错：
```swift
let a= 1 + 2
```
错误信息是：

`error: prefix/postfix '=' is reserved`

意思大概是等号直接跟在前面或后面这种用法是保留的。

下面的代码还是会报错（继续注意空格）：
```swift
let a = 1+ 2
```
错误信息是：

`error: consecutive statements on a line must be separated by ';'`

这是因为Swift认为到1+这个语句就结束了，2就是下一个语句了。

只有这样写才不会报错：
```swift
let a = 1 + 2;  // 编码规范推荐使用这种写法
let b = 3+4 // 这样也是OK的
```
####    整数、浮点数

统一使用 Int 可以提高代码的可复用性，避免不同类型数字之间的转换， 并且匹配数字的类型推断。
示例：
```swift
let minValue = UInt8.min  // minValue 为 0，是 UInt8 类型
let maxValue = UInt8.max  // maxValue 为 255，是 UInt8 类型
```
####    类型安全和类型推断

Swift 是一门类型安全的语言，这意味着 Swift 可以让你清楚地知道值的类型。
如果你没有显式指定类型，Swift 会使用类型推断来选择合适的类型。（int、double）。
示例：
```swift
let meaningOfLife = 42
// meaningOfLife 会被推测为 Int 类型

let pi = 3.14159
// pi 会被推测为 Double 类型
```
####    数值型字面量、数值型类型转换

示例：
```swift
let decimalInteger = 17
let binaryInteger = 0b10001       // 二进制的17
let octalInteger = 0o21           // 八进制的17
let hexadecimalInteger = 0x11     // 十六进制的17
```
####    类型别名

类型别名（type aliases）就是给现有类型定义另一个名字。你可以使用 typealias 关键字来定义类型别名。
示例：
```swift
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound 现在是 0
```
####    布尔值

示例：
```swift
let orangesAreOrange = true
let turnipsAreDelicious = false
```
####    元组

元组（tuples）把多个值组合成一个复合值。元组内的值可以是任意类型，并不要求是相同类型。
示例：
```swift
let http404Error = (404, "Not Found")
// http404Error 的类型是 (Int, String)，值是 (404, "Not Found")
```
####    可选类型

使用可选类型（optionals）来处理值可能缺失的情况。可选类型表示两种可能：或者有值， 你可以解析可选类型访问这个值， 或者根本没有值。
示例：
```swift
var serverResponseCode: Int? = 404
// serverResponseCode 包含一个可选的 Int 值 404
serverResponseCode = nil
// serverResponseCode 现在不包含值
```
####    错误处理

错误处理，应对程序执行中可能会遇到的错误条件。
示例：
```swift
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```
####    断言和先决条件

断言和先决条件，是在运行时所做的检查。
```swift
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
// 因为 age < 0，所以断言会触发
```
####    基本运算符

`Swift 支持大部分标准 C 语言的运算符，还提供了 C 语言没有的区间运算符，例如 a..<b 或 a...b。`
**赋值运算符，算术运算符，组合赋值运算符，比较运算符，三元运算符，空合运算符，区间运算符，逻辑运算符**

运算符分为一元、二元和三元运算符。
闭区间运算符（a...b）定义一个包含从 a 到 b（包括 a 和 b）的所有值的区间。
半开区间运算符（a..<b）定义一个从 a 到 b 但不包括 b 的区间。
闭区间操作符有另一个表达形式，可以表达往一侧无限延伸的区间，(a...，...b)。
示例：
```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("第 \(i + 1) 个人叫 \(names[i])")
}
// 第 1 个人叫 Anna
// 第 2 个人叫 Alex
// 第 3 个人叫 Brian
// 第 4 个人叫 Jack
```
####    字符串和字符
**字符串字面量，字符串插值，计算字符数量，访问和修改字符串，子字符串，比较字符串**

初始化空字符串，字符串可变性，字符串是值类型，连接字符串和字符(+，+=)。
使用字符，可通过 for-in 循环来遍历字符串，获取字符串中每一个字符的值。
字符串插值是一种构建新字符串的方式，可以在其中包含常量、变量、字面量和表达式。可以在已有字符串中插入常量、变量、字面量和表达式从而形成更长的字符串。
Swift 提供了三种方式来比较文本值：字符串字符相等、前缀相等和后缀相等。
示例：
```swift
// 多行字符串字面量
let quotation = """
The White Rabbit put on his spectacles.  "Where shall I begin,
please your Majesty?" he asked.

"Begin at the beginning," the King said gravely, "and go on
till you come to the end; then stop."
"""

// 下面两个字符串其实是一样的
let singleLineString = "These are the same."
let multilineString = """
These are the same.
"""

// 字符串插值
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
// message 是 "3 times 2.5 is 7.5"

// 计算字符数量
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// 打印输出“the number of characters in cafe is 4”

var emptyString = ""               // 空字符串字面量
var anotherEmptyString = String()  // 初始化方法
// 两个字符串均为空并等价。

let catCharacters: [Character] = ["C", "a", "t", "!"]
let catString = String(catCharacters)
print(catString)
// 打印输出：“Cat!”
```
####    集合类型

Swift 语言提供数组（Array）、集合（Set）和字典（Dictionary）三种基本的集合类型用来存储集合数据。数组是有序数据的集。集合是无序无重复数据的集。字典是无序的键值对的集。
**集合的可变性，数组（Arrays），集合（Sets），集合操作，字典**

数组使用有序列表存储同一类型的多个值。相同的值可以多次出现在一个数组的不同位置中。
集合用来存储相同类型并且没有确定顺序的值。当集合元素顺序不重要时或者希望确保每个元素只出现一次时可以使用集合而不是数组。
集合操作，可以高效地完成集合的一些基本操作，比如把两个集合组合到一起，判断两个集合共有元素，或者判断两个集合是否全包含，部分包含或者不相交。
字典是一种无序的集合，它存储的是键值对之间的关系，其所有键的值需要是相同的类型，所有值的类型也需要相同。每个值（value）都关联唯一的键（key），键作为字典中这个值数据的标识符。
示例：
```swift
// 集合
var someInts = [Int]()
print("someInts is of type [Int] with \(someInts.count) items.")
// 打印“someInts is of type [Int] with 0 items.”

var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles 是一种 [Double] 数组，等价于 [0.0, 0.0, 0.0]

var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles 被推断为 [Double]，等价于 [2.5, 2.5, 2.5]
var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles 被推断为 [Double]，等价于 [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]

// enumerated() 方法遍历数组
var shoppingList: [String] = ["Eggs", "Milk"]
for (index, value) in shoppingList.enumerated() {
    print("Item \(String(index + 1)): \(value)")
}
```
####    控制流
**For-In 循环，While 循环（Repeat-While），条件语句，控制转移语句，提前退出（guard），检测 API 可用性**

像 if 语句一样，guard 的执行取决于一个表达式的布尔值。我们可以使用 guard 语句来要求条件必须为真时，以执行 guard 语句后的代码。不同于 if 语句，一个 guard 语句总是有一个 else 从句，如果条件不为真则执行 else 从句中的代码。
Swift 内置支持检查 API 可用性，编译器使用 SDK 中的可用信息来验证我们的代码中使用的所有 API 在项目指定的部署目标上是否可用。如果我们尝试使用一个不可用的 API，Swift 会在编译时报错。
示例：
```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}

let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
for (animalName, legCount) in numberOfLegs {
    print("\(animalName)s have \(legCount) legs")
}

//  repeat-while 循环的一般格式
repeat {
    statements
} while condition


// 提前退出
func greet(person: [String: String]) {
    guard let name = person["name"] else {
        return
    }

    print("Hello \(name)!")

    guard let location = person["location"] else {
        print("I hope the weather is nice near you.")
        return
    }

    print("I hope the weather is nice in \(location).")
}
greet(person: ["name": "John"])
// 输出“Hello John!”
// 输出“I hope the weather is nice near you.”
greet(person: ["name": "Jane", "location": "Cupertino"])
// 输出“Hello Jane!”
// 输出“I hope the weather is nice in Cupertino.”
```
####    函数
**函数的定义与调用，函数参数与返回值，函数参数标签和参数名称，函数类型，嵌套函数**

可选元组返回类型。
定义一个输入输出参数时，在参数定义前加 inout 关键字。
示例：
```swift
// 函数
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}

func greet(person: String, from hometown: String) -> String {
    return "Hello \(person)!  Glad you could visit from \(hometown)."
}
print(greet(person: "Bill", from: "Cupertino"))
// 打印“Hello Bill!  Glad you could visit from Cupertino.”

// 可选元组返回类型
func minMax(array: [Int]) -> (min: Int, max: Int)? {
    if array.isEmpty { return nil }
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}

// 隐式返回的函数
func greeting(for person: String) -> String {
    "Hello, " + person + "!"
}
print(greeting(for: "Dave"))
// 打印 "Hello, Dave!

// 参数标签
func greet(person: String, from hometown: String) -> String {
    return "Hello \(person)!  Glad you could visit from \(hometown)."
}
print(greet(person: "Bill", from: "Cupertino"))
// 打印“Hello Bill!  Glad you could visit from Cupertino.”
```
####    闭包

闭包是自包含的函数代码块，可以在代码中被传递和使用。与一些编程语言中的匿名函数（Lambdas）比较相似。
**闭包表达式，尾随闭包，值捕获，闭包是引用类型，逃逸闭包（@escaping），自动闭包**

如果你需要将一个很长的闭包表达式作为最后一个参数传递给函数，将这个闭包替换成为尾随闭包的形式很有用。
闭包可以在其被定义的上下文中捕获常量或变量。即使定义这些常量和变量的原作用域已经不存在，闭包仍然可以在闭包函数体内引用和修改这些值。
示例：
```swift
// 闭包表达式语法
{ (parameters) -> return type in
    statements
}

// 尾随闭包
let digitNames = [
    0: "Zero", 1: "One", 2: "Two",   3: "Three", 4: "Four",
    5: "Five", 6: "Six", 7: "Seven", 8: "Eight", 9: "Nine"
]
let numbers = [16, 58, 510]
let strings = numbers.map {
    (number) -> String in
    var number = number
    var output = ""
    repeat {
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
    return output
}
// strings 常量被推断为字符串类型数组，即 [String]
// 其值为 ["OneSix", "FiveEight", "FiveOneZero"]

// 值捕获
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}

// 自动闭包，延迟求值
var customersInLine = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
print(customersInLine.count)
// 打印出“5”

let customerProvider = { customersInLine.remove(at: 0) }
print(customersInLine.count)
// 打印出“5”

print("Now serving \(customerProvider())!")
// Prints "Now serving Chris!"
print(customersInLine.count)
// 打印出“4”
```
####    枚举

使用 enum 关键词来创建枚举并且把它们的整个定义放在一对大括号内。
**枚举语法，使用 Switch 语句匹配枚举值，枚举成员的遍历，关联值，原始值（默认值），递归枚举（indirect）**

可以定义 Swift 枚举来存储任意类型的关联值，每个枚举成员的关联值类型可以各不相同。
示例：
```swift
// 枚举语法
enum SomeEnumeration {
    // 枚举定义放在这里
}

enum CompassPoint {
    case north
    case south
    case east
    case west
}

enum Planet {
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune
}

let somePlanet = Planet.earth
switch somePlanet {
case .earth:
    print("Mostly harmless")
default:
    print("Not a safe place for humans")
}
// 打印“Mostly harmless”

// 关联值
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
var productBarcode = Barcode.upc(8, 85909, 51226, 3)
productBarcode = .qrCode("ABCDEFGHIJKLMNOP")

switch productBarcode {
case let .upc(numberSystem, manufacturer, product, check):
    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
case let .qrCode(productCode):
    print("QR code: \(productCode).")
}
// 打印“QR code: ABCDEFGHIJKLMNOP.”

// 递归枚举
indirect enum ArithmeticExpression {
    case number(Int)
    case addition(ArithmeticExpression, ArithmeticExpression)
    case multiplication(ArithmeticExpression, ArithmeticExpression)
}
let five = ArithmeticExpression.number(5)
let four = ArithmeticExpression.number(4)
let sum = ArithmeticExpression.addition(five, four)
let product = ArithmeticExpression.multiplication(sum, ArithmeticExpression.number(2))
// (5 + 4) * 2

func evaluate(_ expression: ArithmeticExpression) -> Int {
    switch expression {
    case let .number(value):
        return value
    case let .addition(left, right):
        return evaluate(left) + evaluate(right)
    case let .multiplication(left, right):
        return evaluate(left) * evaluate(right)
    }
}

print(evaluate(product))
// 打印“18”
```
####    结构体和类
**结构体和类对比，结构体和枚举是值类型，类是引用类型**

结构体和类作为一种通用而又灵活的结构，成为了人们构建代码的基础。你可以使用定义常量、变量和函数的语法，为你的结构体和类定义属性、添加方法。
示例：
```swift
// 类和结构体
struct SomeStructure {
    // 在这里定义结构体
}
class SomeClass {
    // 在这里定义类
}

struct Resolution {
    var width = 0
    var height = 0
}
class VideoMode {
    var resolution = Resolution()
    var interlaced = false
    var frameRate = 0.0
    var name: String?
}
```
####    属性
**存储属性，计算属性，属性观察器，属性包装器，全局变量和局部变量，类型属性（static）**

属性将值与特定的类、结构体或枚举关联。存储属性会将常量和变量存储为实例的一部分，而计算属性则是直接计算（而不是存储）值。计算属性可以用于类、结构体和枚举，而存储属性只能用于类和结构体。
属性观察器监控和响应属性值的变化，每次属性被设置值的时候都会调用属性观察器，即使新值和当前值相同的时候也不例外。

*    willSet 在新的值被设置之前调用
*    didSet 在新的值被设置之后调用

属性包装器在管理属性如何存储和定义属性的代码之间添加了一个分隔层。
类型属性也是通过点运算符来访问。但是，类型属性是通过类型本身来访问，而不是通过实例。
示例：
```swift
// 属性
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()       //存储属性
    var center: Point {     //计算型属性
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
    size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
// 打印“square.origin is now at (10.0, 10.0)”

// 属性包装器
@propertyWrapper
struct TwelveOrLess {
    private var number = 0
    var wrappedValue: Int {
        get { return number }
        set { number = min(newValue, 12) }
    }
}
```
####    方法
**实例方法（Instance Methods），类型方法（static）**

方法是与某些特定类型相关联的函数。
类、结构体、枚举都可以定义实例方法；实例方法为给定类型的实例封装了具体的任务与功能。
类、结构体、枚举也可以定义类型方法；类型方法与类型本身相关联。
示例：
```swift
// 方法
class Counter {
    var count = 0
    func increment() {
        count += 1
    }
    func increment(by amount: Int) {
        count += amount
    }
    func reset() {
        count = 0
    }
}
```
####    下标

下标可以定义在类、结构体和枚举中，是访问集合、列表或序列中元素的快捷方式
下标语法（subscript），下标用法，下标选项，类型下标（static）
```swift
subscript(index: Int) -> Int {
    get {
      // 返回一个适当的 Int 类型的值
    }
    set(newValue) {
      // 执行适当的赋值操作
    }
}

// 示例
struct TimesTable {
    let multiplier: Int
    subscript(index: Int) -> Int {
        return multiplier * index
    }
}
let threeTimesTable = TimesTable(multiplier: 3)
print("six times three is \(threeTimesTable[6])")
// 打印“six times three is 18”

var numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
numberOfLegs["bird"] = 2

// 类型下标
enum Planet: Int {
    case mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune
    static subscript(n: Int) -> Planet {
        return Planet(rawValue: n)!
    }
}
let mars = Planet[4]
print(mars)
```
####    继承
**定义一个基类，子类生成，重写(override)，防止重写(final)**

不继承于其它类的类，称之为基类。
示例：
```swift
// 继承
class SomeClass: SomeSuperclass {
    // 这里是子类的定义
}

class Vehicle {
    var currentSpeed = 0.0
    var description: String {
        return "traveling at \(currentSpeed) miles per hour"
    }
    func makeNoise() {
        // 什么也不做——因为车辆不一定会有噪音
    }
}

class Car: Vehicle {
    var gear = 1
    override var description: String {
        return super.description + " in gear \(gear)"
    }
}

class AutomaticCar: Car {
    override var currentSpeed: Double {
        didSet {
            gear = Int(currentSpeed / 10.0) + 1
        }
    }
}
```
####    构造过程

构造过程是使用类、结构体或枚举类型的实例之前的准备过程。
**存储属性的初始赋值，自定义构造过程，默认构造器，值类型的构造器代理，类的继承和构造过程，可失败构造器，必要构造器（required）**

构造器可以通过调用其它构造器来完成实例的部分构造过程。这一过程称为构造器代理，它能避免多个构造器间的代码重复。
Swift 为类类型提供了两种构造器来确保实例中所有存储型属性都能获得初始值，它们被称为指定构造器和便利构造器。
可以在一个类，结构体或是枚举类型的定义中，添加一个或多个可失败构造器。其语法为在 init 关键字后面添加问号（init?）。
必要构造器，在类的构造器前添加 required 修饰符表明所有该类的子类都必须实现该构造器。
示例：
```swift
// 构造过程
init() {
    // 在此处执行构造过程
}

struct Fahrenheit {
    var temperature: Double
    init() {
        temperature = 32.0
    }
}
var f = Fahrenheit()
print("The default temperature is \(f.temperature)° Fahrenheit")
// 打印“The default temperature is 32.0° Fahrenheit”

struct Color {
    let red, green, blue: Double
    init(red: Double, green: Double, blue: Double) {
        self.red   = red
        self.green = green
        self.blue  = blue
    }
    init(white: Double) {
        red   = white
        green = white
        blue  = white
    }
}
```
####    析构过程

析构器只适用于类类型，当一个类的实例被释放之前，析构器会被立即调用。析构器用关键字 deinit 来标示，类似于构造器要用 init 来标示。
Swift 会自动释放不再需要的实例以释放资源。
示例：
```swift
// 析构过程
deinit {
    // 执行析构过程
}

class Bank {
    static var coinsInBank = 10_000
    static func distribute(coins numberOfCoinsRequested: Int) -> Int {
        let numberOfCoinsToVend = min(numberOfCoinsRequested, coinsInBank)
        coinsInBank -= numberOfCoinsToVend
        return numberOfCoinsToVend
    }
    static func receive(coins: Int) {
        coinsInBank += coins
    }
}

class Player {
    var coinsInPurse: Int
    init(coins: Int) {
        coinsInPurse = Bank.distribute(coins: coins)
    }
    func win(coins: Int) {
        coinsInPurse += Bank.distribute(coins: coins)
    }
    deinit {
        Bank.receive(coins: coinsInPurse)
    }
}
```
####    可选链式调用

可选链式调用是一种可以在当前值可能为 nil 的可选值上请求和调用属性、方法及下标的方法。
通过在想调用的属性、方法，或下标的可选值后面放一个问号（?），可以定义一个可选链。类似在可选值后面放一个叹号（!）来强制展开它的值。它们的主要区别在于当可选值为空时可选链式调用只会调用失败，然而强制展开将会触发运行时错误。
示例：
```swift
class Person {
    var residence: Residence?
}

class Residence {
    var numberOfRooms = 1
}
let john = Person()
let roomCount = john.residence!.numberOfRooms
// 这会引发运行时错误

if let roomCount = john.residence?.numberOfRooms {
    print("John's residence has \(roomCount) room(s).")
} else {
    print("Unable to retrieve the number of rooms.")
}
// 打印“Unable to retrieve the number of rooms.”

john.residence = Residence()

if let roomCount = john.residence?.numberOfRooms {
    print("John's residence has \(roomCount) room(s).")
} else {
    print("Unable to retrieve the number of rooms.")
}
// 打印“John's residence has 1 room(s).”
```
####    错误处理

错误处理（Error handling） 是响应错误以及从错误中恢复的过程。Swift 在运行时提供了抛出、捕获、传递和操作可恢复错误（recoverable errors）的一等支持。
**表示与抛出错误，处理错误，指定清理操作**

在 Swift 中，错误用遵循 Error 协议的类型的值来表示。
Swift 中有 4 种处理错误的方式。可以把函数抛出的错误传递给调用此函数的代码（throws）、用 do-catch 语句处理错误、将错误作为可选类型处理（try?）、或者断言此错误根本不会发生（try!）。
defer 语句将代码的执行延迟到当前的作用域退出之前。
示例：
```swift
// 错误处理
enum VendingMachineError: Error {
    case invalidSelection                     //选择无效
    case insufficientFunds(coinsNeeded: Int) //金额不足
    case outOfStock                             //缺货
}
throw VendingMachineError.insufficientFunds(coinsNeeded: 5)

var vendingMachine = VendingMachine()
vendingMachine.coinsDeposited = 8
do {
    try buyFavoriteSnack(person: "Alice", vendingMachine: vendingMachine)
    print("Success! Yum.")
} catch VendingMachineError.invalidSelection {
    print("Invalid Selection.")
} catch VendingMachineError.outOfStock {
    print("Out of Stock.")
} catch VendingMachineError.insufficientFunds(let coinsNeeded) {
    print("Insufficient funds. Please insert an additional \(coinsNeeded) coins.")
} catch {
    print("Unexpected error: \(error).")
}
// 打印“Insufficient funds. Please insert an additional 2 coins.”

// 指定清理操作
func processFile(filename: String) throws {
    if exists(filename) {
        let file = open(filename)
        defer {
            close(file)
        }
        while let line = try file.readline() {
            // 处理文件。
        }
        // close(file) 会在这里被调用，即作用域的最后。
    }
}
```
####    类型转换

类型转换在 Swift 中使用 is 和 as 操作符实现。这两个操作符分别提供了一种简单达意的方式去检查值的类型或者转换它的类型。
**为类型转换定义类层次，检查类型（is），向下转型（as? 或 as!），Any 和 AnyObject 的类型转换**

可以将类型转换用在类和子类的层次结构上，检查特定类实例的类型并且转换这个类实例的类型成为这个层次结构中的其他类型。
Swift 为不确定类型提供了两种特殊的类型别名：

*    Any 可以表示任何类型，包括函数类型。

*    AnyObject 可以表示任何类类型的实例。

示例：
```swift
// 类型转换
// 一个基类 MediaItem
class MediaItem {
 var name: String
 init(name: String) {
  self.name = name
 }
}

class Movie: MediaItem {
 var director: String
 init(name: String, director: String) {
  self.director = director
  super.init(name: name)
 }
}

class Song: MediaItem {
 var artist: String
 init(name: String, artist: String) {
  self.srtist = artist
  super.init(name: name)
 }
}

let library = [
 Movie(name: "Casablanca", director: "Micheal Curtiz"),
 Song(name: "Blue Suede Shose", artist: "Elvis Presley"),
 Movie(name: "Citizen Kane", director: "Orson Wells"),
 Song(name: "The One And Only", artist: "Chesney Hawkes"),
 Song(name: "Never Gonna Give You Up", artist: "Rick Astley")
]
var movieCount = 0
var songCount = 0

for item in library {
 if item is Movie {
  movieCount += 1
 } else if item is Song {
  songCount += 1
 }
}

print("Media library contains \(movieCount) movies and \(songCount)")
// 打印“Media library contains 2 movies and 3 songs”

for item in library {
 if let movie = item as? Movie {
  print("Movie: \(movie.name), dir. \(movie.director)")
 } else if let song = item as? Song {
  print("Song: \(song.name), by \(song.artist)")
 }
}
// Movie: Casablanca, dir. Michael Curtiz
// Song: Blue Suede Shoes, by Elvis Presley
// Movie: Citizen Kane, dir. Orson Welles
// Song: The One And Only, by Chesney Hawkes
// Song: Never Gonna Give You Up, by Rick Astley
```
####    嵌套类型

Swift 允许定义嵌套类型，可以在支持的类型中定义嵌套的枚举、类和结构体。
**嵌套类型实践，引用嵌套类型**

要在一个类型中嵌套另一个类型，将嵌套类型的定义写在其外部类型的 {} 内，而且可以根据需要定义多级嵌套。
示例：
```swift
// 嵌套类型
stuct BlackjackCard {
 // 嵌套的 Suit 枚举
 enum Suit: Character {
  case spades = "1", hearts = "2", diamonds = "3", clubs = "4"
 }
 
 // 嵌套的 Rank 枚举
 enum Rank: Int {
  case two = 2, three, four, five, six, seven, eight, nine, ten
  case jack, queen, king, ace
  struct Values {
   let first: Int, second: Int?
  }
  var values: Values {
   switch self {
   case .ace:
    return Values(first: 1, second: 11)
   case .jack, .queen, .king:
    return Values(first: 10, second: nil)
   default:
    return Values(first: self.rawValue, second: nil)
   }
  }
 }
 
 // BlackjackCard 的属性和方法
 let rank: Rank, suit: Suit
 var description: String {
  var output = "suit is \(suit.rawValue),"
  output += " value is \(rank.values.first)"
  if let second = rank.values.second {
   output += " or \(second)"
  }
  return output
 }
}

let theAceOfSpades = BlackjackCard(rank: .ace, suit: .spades)
print("theAceOfSpades: \(theAceOfSpades.description)")
// 打印“theAceOfSpades: suit is 1, value is 1 or 11”

let heartsSymbol = BlackjackCard.Suit.hearts.rawValue
// 2
```
####    扩展

扩展可以给一个现有的类，结构体，枚举，还有协议添加新的功能。
**扩展的语法，计算型属性，构造器，方法，下标，嵌套类型**

Swift 中的扩展可以：

*    添加计算型实例属性和计算型类属性

*    定义实例方法和类方法

*    提供新的构造器

*    定义下标

*    定义和使用新的嵌套类型

*    使已经存在的类型遵循（conform）一个协议

扩展语法:
```swift
extension SomeType {
  // 在这里给 SomeType 添加新的功能
}
```
扩展可以给现有类型添加计算型实例属性和计算型类属性。
扩展可以给现有的类型添加新的构造器。
扩展可以给现有类型添加新的实例方法和类方法。
扩展可以给现有的类型添加新的下标。
扩展可以给现有的类，结构体，还有枚举添加新的嵌套类型。
示例：
```swift
// 扩展的语法
extension SomeType {
  // 在这里给 SomeType 添加新的功能
}
// 添加一个或多个协议
extension SomeType: SomeProtocol, AnotherProtocol {
  // 协议所需要的实现写在这里
}

struct Size {
 var width = 0.0, height = 0.0
}
struct Point {
 var x = 0.0, y = 0.0
}
struct Rect {
 var origin = Point()
 var size = Size()
}

extension Rect {
 init(center: Point, size: Size) {
  let originX = center.x - (size.width / 2)
  let originY = center.y - (size.height / 3)
  self.init(origin: Point(x: originX, y: originY), size: size)
 }
}
let centerRect = Rect(center: Point(x: 4.0, y: 4.0), 
 size: Size(width: 3.0, height: 3.0))
// centerRect 的 origin 是 (2.5, 2.5) 并且它的 size 是 (3.0, 3.0)

extension Int {
 func repetitions(task: () -> Void) {
  for _ in 0..<self {
   task()
  }
 }
}
3.repetitions {
 print("Hello!")
}
// Hello!
// Hello!
// Hello!

extension Int {
 mutating func square() {
  self = self * self
 }
}
var somtInt = 3
someInt.square()
// someInt 现在是9
```
####    协议

协议定义了一个蓝图，规定了用来实现某一特定任务或者功能的方法、属性，以及其他需要的东西。
类、结构体或枚举都可以遵循协议，并为协议定义的这些要求提供具体实现。
协议语法，属性要求，方法要求，异变方法要求，构造器要求，协议作为类型，委托，协议类型的集合，协议的继承，类专属的协议，协议合成，检查协议一致性，可选的协议要求，协议扩展，

协议语法
```swift
protocol SomeProtocol {
    // 这里是协议的定义部分
}
```
协议可以要求遵循协议的类型提供特定名称和类型的实例属性或类型属性。
协议可以要求遵循协议的类型实现某些指定的实例方法或类方法。
在值类型（即结构体和枚举）的实例方法中，将 mutating 关键字作为方法的前缀，写在 func 关键字之前，表示可以在该方法中修改它所属的实例以及实例的任意属性的值。
协议可以要求遵循协议的类型实现指定的构造器。
委托是一种设计模式，它允许类或结构体将一些需要它们负责的功能委托给其他类型的实例。
示例：
```swift
// 协议语法
protocol SomeProtocol {
    // 这里是协议的定义部分
}

struct SomeStructure: FirstProtocol, AnotherProtocol {
 // 这里是结构体的定义部分
}

class SomeClass: SomeSuperClass, FirstProtocol, AnotherProtocol {
 // 这里是类的定义部分
}

protocol SomeProtocol {
 var mustBeSettable: Int { get set }
 var doesNotNeedToBeSettable: Int { get }
}

protocol AnotherProtocol {
 static var someTypeProperty: Int { get set }
}

protocol FullyNamed {
 var fullName: String { get }
}

struct person: FullyNamed {
 var fullName: String
}
let john = Person(fullName: "John Appleseed")
// john.fullName 为 "John Appleseed"

class Starship: FullyNamed {
 var prefix: String?
 var name: String
 init(name: String, prefix: String? = nil) {
  self.name = name
  self.prefix = prefix
 }
 
 var fullName: String {
  return (prefix != nil ? prefix! + " " : "") + name
 }
}
var ncc1701 = Starship(name: "Enterprise", prefix: "USS")
// ncc1701.fullName 为 "USS Enterprise"
```
####    泛型

泛型代码让你能根据自定义的需求，编写出适用于任意类型的、灵活可复用的函数及类型。
你可避免编写重复的代码，而是用一种清晰抽象的方式来表达代码的意图。
**泛型函数，类型参数，命名类型参数，泛型类型，泛型扩展，类型约束，关联类型**

示例：
```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}

func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}

func swapTwoInts(_ a: inout Int, _ b: inout Int)
func swapTwoValues<T>(_ a: inout T, _ b: inout T)

var someInt = 3
var anotherInt = 107
swapTwoValues(&someInt, &anotherInt)
// someInt 现在是 107，anotherInt 现在是 3

var someString = "hello"
var anotherString = "world"
swapTwoValues(&someString, &anotherString)
// someString 现在是“world”，anotherString 现在是“hello”
```
####    不透明类型

具有不透明返回类型的函数或方法会隐藏返回值的类型信息。
函数不再提供具体的类型作为返回类型，而是根据它支持的协议来描述返回值。
**不透明类型解决的问题，返回不透明类型，不透明类型和协议类型的区别**

在处理模块和调用代码之间的关系时，隐藏类型信息非常有用，因为返回的底层数据类型仍然可以保持私有。
不透明类型和泛型相反。不透明类型允许函数实现时，选择一个与调用代码无关的返回类型。
如果函数中有多个地方返回了不透明类型，那么所有可能的返回值都必须是同一类型。返回不透明类型和返回协议类型主要区别，就在于是否需要保证类型一致性。
一个不透明类型只能对应一个具体的类型，即便函数调用者并不能知道是哪一种类型；协议类型可以同时对应多个类型，只要它们都遵循同一协议。
示例：
```swift
protocol Shape {
    func draw() -> String
}

struct Triangle: Shape {
    var size: Int
    func draw() -> String {
        var result = [String]()
        for length in 1...size {
            result.append(String(repeating: "*", count: length))
        }
        return result.joined(separator: "\n")
    }
}
let smallTriangle = Triangle(size: 3)
print(smallTriangle.draw())
// *
// **
// ***

struct FlippedShape<T: Shape>: Shape {
    var shape: T
    func draw() -> String {
        let lines = shape.draw().split(separator: "\n")
        return lines.reversed().joined(separator: "\n")
    }
}
let flippedTriangle = FlippedShape(shape: smallTriangle)
print(flippedTriangle.draw())
// ***
// **
// *
```
####    自动引用计数

Swift 使用自动引用计数（ARC）机制来跟踪和管理你的应用程序的内存。
如果两个类实例互相持有对方的强引用，因而每个实例都让对方一直存在，就是这种情况。这就是所谓的循环强引用。
Swift提供了两种办法用来解决你在使用类的属性时所遇到的循环强引用问题：弱引用（weak reference）和无主引用（unowned reference）。

*    声明属性或者变量时，在前面加上 weak 关键字表明这是一个弱引用。

*    声明属性或者变量时，在前面加上关键字 unowned 表示这是一个无主引用。

示例：
```swift
// 自动引用计数实践
class Person {
    let name: String
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}

var reference1: Person?
var reference2: Person?
var reference3: Person?
reference1 = Person(name: "John Appleseed")
// 打印“John Appleseed is being initialized”
reference2 = reference1
reference3 = reference1
reference1 = nil
reference2 = nil
reference3 = nil
// 打印“John Appleseed is being deinitialized”

// 循环强引用
class Person {
    let name: String
    init(name: String) { self.name = name }
    var apartment: Apartment?
    deinit { print("\(name) is being deinitialized") }
}

class Apartment {
    let unit: String
    init(unit: String) { self.unit = unit }
    var tenant: Person?
    deinit { print("Apartment \(unit) is being deinitialized") }
}
var john: Person?
var unit4A: Apartment?
john = Person(name: "John Appleseed")
unit4A = Apartment(unit: "4A")

john = nil
unit4A = nil

// 弱引用
class Person {
    let name: String
    init(name: String) { self.name = name }
    var apartment: Apartment?
    deinit { print("\(name) is being deinitialized") }
}

class Apartment {
    let unit: String
    init(unit: String) { self.unit = unit }
    weak var tenant: Person?
    deinit { print("Apartment \(unit) is being deinitialized") }
}

var john: Person?
var unit4A: Apartment?

john = Person(name: "John Appleseed")
unit4A = Apartment(unit: "4A")

john!.apartment = unit4A
unit4A!.tenant = john

john = nil
// 打印“John Appleseed is being deinitialized”
```
####    内存安全

默认情况下，Swift 会阻止你代码里不安全的行为。
理解内存访问冲突，In-Out 参数的访问冲突，方法里 self 的访问冲突，属性的访问冲突

示例：
```swift
func balance(_ x: inout Int, _ y: inout Int) {
    let sum = x + y
    x = sum / 2
    y = sum - x
}
var playerOneScore = 42
var playerTwoScore = 30
balance(&playerOneScore, &playerTwoScore)  // 正常
balance(&playerOneScore, &playerOneScore)
// 错误：playerOneScore 访问冲突
```
####    访问控制

访问控制可以限定其它源文件或模块对你的代码的访问。

*    open 和 public 级别可以让实体被同一模块源文件中的所有实体访问，在模块外也可以通过导入该模块来访问源文件里的所有实体。通常情况下，你会使用 open 或 public 级别来指定框架的外部接口。

*    internal 级别让实体被同一模块源文件中的任何实体访问，但是不能被模块外的实体访问。通常情况下，如果某个接口只在应用程序或框架内部使用，就可以将其设置为 internal 级别。

*    fileprivate 限制实体只能在其定义的文件内部访问。如果功能的部分实现细节只需要在文件内使用时，可以使用 fileprivate 来将其隐藏。

*    private 限制实体只能在其定义的作用域，以及同一文件内的 extension 访问。如果功能的部分细节只需要在当前作用域内使用时，可以使用 private 来将其隐藏。

open 为最高访问级别（限制最少），private 为最低访问级别（限制最多）。
open 只能作用于类和类的成员，它和 public 的区别主要在于 open 限定的类和成员能够在模块外能被继承和重写。
示例：
```swift
public class SomePublicClass {}
internal class SomeInternalClass {}
fileprivate class SomeFilePrivateClass {}
private class SomePrivateClass {}

class SomeInternalClass {}   // 隐式 internal
var someInternalConstant = 0 // 隐式 internal

public class SomePublicClass {                  // 显式 public 类
    public var somePublicProperty = 0            // 显式 public 类成员
    var someInternalProperty = 0                 // 隐式 internal 类成员
    fileprivate func someFilePrivateMethod() {}  // 显式 fileprivate 类成员
    private func somePrivateMethod() {}          // 显式 private 类成员
}

class SomeInternalClass {                       // 隐式 internal 类
    var someInternalProperty = 0                 // 隐式 internal 类成员
    fileprivate func someFilePrivateMethod() {}  // 显式 fileprivate 类成员
    private func somePrivateMethod() {}          // 显式 private 类成员
}

fileprivate class SomeFilePrivateClass {        // 显式 fileprivate 类
    func someFilePrivateMethod() {}              // 隐式 fileprivate 类成员
    private func somePrivateMethod() {}          // 显式 private 类成员
}

private class SomePrivateClass {                // 显式 private 类
    func somePrivateMethod() {}                  // 隐式 private 类成员
}
```
####    高级运算符

Swift还提供了数种可以对数值进行复杂运算的高级运算符。它们包含了位运算符和移位运算符。
**位运算符、溢出运算符、优先级和结合性、运算符函数、自定义运算符**

示例：
```swift
let initialBits: UInt8 = 0b00001111
let invertedBits = ~initialBits // 等于 0b11110000

var potentialOverflow = Int16.max
// potentialOverflow 的值是 32767，这是 Int16 能容纳的最大整数
potentialOverflow += 1
// 这里会报错

struct Vector2D {
    var x = 0.0, y = 0.0
}

extension Vector2D {
    static func + (left: Vector2D, right: Vector2D) -> Vector2D {
        return Vector2D(x: left.x + right.x, y: left.y + right.y)
    }
}

let vector = Vector2D(x: 3.0, y: 1.0)
let anotherVector = Vector2D(x: 2.0, y: 4.0)
let combinedVector = vector + anotherVector
// combinedVector 是一个新的 Vector2D 实例，值为 (5.0, 5.0)
```
