
#读源码学Swift编程 之Alamofire


#Request.swift





-  internal(set)  设置set权限
<pre>
open internal(set) var delegate: TaskDelegate
</pre>

- defer

<pre>
open internal(set) var delegate: TaskDelegate {
        get {
            taskDelegateLock.lock() ; defer { taskDelegateLock.unlock() }
            return taskDelegate
        }
        set {
            taskDelegateLock.lock() ; defer { taskDelegateLock.unlock() }
            taskDelegate = newValue
        }
    }

</pre>

***解读***

起到延时作用，在定义的当前作用域最后一步执行

注意：类中使用defer,在对象方法中,使用defer,在defer块中,调用属性之前,必须初始化所有存储属性,重要事说三遍,所有的存储属性,所有的,存储属性

- @discardableResult

<pre>

 @discardableResult
    open func authenticate(
        user: String,
        password: String,
        persistence: URLCredential.Persistence = .forSession)
        -> Self
    {
        let credential = URLCredential(user: user, password: password, persistence: persistence)
        return authenticate(usingCredential: credential)
    }
</pre>

***解读***

函数的setNewScore 方法有返回值,但是调用的时候,没有使用常量或者变量接受这个返回值,系统会产生警告如下图；通过加关键字@discardableResult去除那种警告


- os宏
  
  if os(OSX) || os(iOS) || os(tvOS) || os(watchOS)
  
  ***解读***
  
  系统版本检测

- @escaping

***解读***

我们经常在下载等异步操作完成时,才调用闭包函数,我们有可能暂时不要把这个闭包存放在数组中,或者使用属性去引用它,那么这个时候就需要使用这个关键了；

默认为：nonescape



- CustomStringConvertible
- CustomDebugStringConvertible 

***解读***

在调试的时候总会发现在输出自定义的类与结构体时,会打印很多不想输出的变量；

<https://developer.apple.com/reference/swift/customstringconvertible>

- AnyHashable
<pre>
     var headers: [AnyHashable: Any] = [:]

</pre>

***解读***
A type-erased hashable value. 类型擦除

<https://developer.apple.com/reference/swift/anyhashable>
- OptionSet





   