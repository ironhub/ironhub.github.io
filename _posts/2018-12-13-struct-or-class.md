---
layout: post 

title: struct or class 

date: 2018-12-13 

author: C.W.Kim 

categories: Swift 

tags: swift 
---
### struct or class ### 
> Architecture is ... 
#### struct or class #### 
> description  
* Independent **deployable** services 
* Highly decoupled 
```swift 
// swift sentence 
```



Learn how to build iOS apps
Get started with iOS 12 and Swift 4
Sign up for our iOS development course Zero to App Store and learn how to build professional iOS 12 apps with Swift 4 and Xcode 10.

Learn MoreStart for Free
Structs Are Awesome
So what are structs good for? It’s preferrable to use structs in these cases:

For values that are small and easy to copy. Think about database objects you want to pass around in your code, like NewsItem, Task or User. Since they’re so small and well-defined, it’s much easier to pass them around as structs.
In a multi-threaded environment, for instance with a database connection that’s opened in a different thread, structs are safer. They can be copied from one thread to another thread, without running the risk of a race condition or deadlock. Classes do not have this inherent safety, unless they’re deliberately made thread-safe.
When the properties of a struct are mostly value types too, like String, it makes sense to wrap them in a struct instead of a class.
When you don’t need inheritance, or want to use Protocol Oriented Programming, it makes sense to use structs, too.

Just so we’re on the same page, this is how you define and use a struct:

struct NewsItem
{
​    var title:String = ""
​    var url:String = ""
}

var item = NewsItem()
item.title = "Comparing Classes vs. Structs in Swift"
item.url = "https://learnappmaking.com/classes-structs-comparison-swift-programming"

print(item)
// Output: NewsItem(title: "Comparing Classes vs. Structs in Swift", url: "https://learnappmaking.com/classes-structs-comparison-swift-programming")
As you can see, the syntax is effectively the same as for defining and using a class. Instead of class [name] { ... you write struct [name] { ....

Speaking of classes…

What Classes Are Good For
What are classes good for, if you have structs? As noted before, classes have a few extra characteristics that structs don’t have:

Classes can inherit from another class, which you can’t do with structs. With classes, you can write class MyViewController : UIViewController to create a subclass of UIViewController. Conversely, structs can implement protocols.
Classes can be deinitialized, i.e. they can implement a deinit function, and you can make one or more references to the same class (i.e., classes are a reference type).
Inheritance is the most important difference between classes and struct. With classes, you can clearly define a parent-child connection between subclass and superclass.

A few examples:

MyViewController inherits from UIViewController
MyTableViewController inherits from InfiniteTableViewController to adopt “infinite scrolling”, which in turn inherits from UITableViewController
Car and Bike both inherit from Vehicle, because they both use the same “basic” set of characteristics like numberOfWheels and speed.
In these last two examples lies a danger: you can end up with a whole bunch of inherited classes, that all “decorate” the subclass with different functionalities. Think about SuperCar and MuscleCar, that both inherit from Car, and from Vehicle.

It’s easy to get lost in which class inherits what, even though, at first sight, it makes sense to structure your classes like this. What if SuperCar inherits a function that it doesn’t need from Vehicle? What if you want to create a SuperBike, that’s similar to a SuperCar, but you can’t “inherit” or share those characteristics because they’re in different subclass-superclass hierarchies?

As a rule of thumb, it only makes sense to use classes for these scenarios1:

When copying or comparing instances doesn’t make sense, e.g. with Window or UIViewController. It doesn’t make sense to copy an app window, since there’s only one active at a time, and it often doesn’t make sense to copy a view controller either – you’d just create a new one.
When the “lifetime” of an instance is tied to external effects, e.g. for DatabaseConnection or TemporaryFile. It doesn’t make sense to create two copies of a reference to a file on the disk, after all, they both reference the same data, and represent that data in code. (You don’t write a phone number twice in an address book, right?)
When instances are just “conduits” for external states, e.g. for CGContext. Sometimes you need a helper or wrapper class to get things done: an API or a reference to an online resource. In those cases the class is only a conduit, something that passes along information, and it doesn’t make sense to create a copy of that.
As you can see, “to copy, or to reference” is the defining factor to choose between classes or structs. If it makes sense to copy a value, pick structs, if it makes sense to reference a value (and not copy), then choose classes.

