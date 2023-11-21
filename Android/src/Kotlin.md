# Kotlin上手

## 引入kotlin

* 根目录
  ```gradle
   buildscript {
     👇
     ext.kotlin_version = '1.3.41'
        repositories {
             ...
        }
        dependencies {
           classpath 'com.android.tools.build:gradle:3.5.0-beta05'
             👇
             classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
         }
    }
  ```
* app目录

```gradle
apply plugin: 'com.android.application'
     👇
     apply plugin: 'kotlin-android'
     ...
     
     android {
         ...
     }
     
     dependencies {
         implementation fileTree(dir: 'libs', include: ['*.jar'])
         👇
         implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:$kotlin_version"
         ...
}
```
## 声明：`val` `var` `.?`

* 对象声明和类型推断 `val a:String = "name"`  `var a = "name"`

* 解除非空限制 `var a:String ?= null `调用时使用`a?.`
* 懒加载`lateinit`

## 函数

```kotlin
//返回void,可空参数
fun main(name:String?): Unit {}
//Unit省略
fun main(){}
```

## 对象

```kotlin
class Stu{
    //构造方法
    constructor(){
    }
    var name: String? = null
        //钩子
        get() = "我是$field"
        set(value: String?){
            field = value+field
        }
    var age:Int = 0
}
```
* 默认可见性 `public`
* `override`关键字代替注解，可遗传，通过添加final禁止遗传
* 默认不可继承，`open`关键字可继承
* 抽象类`abstract`关键字
* `is`关键字代替`instanceof`判断类型，自动强转
* `as`关键字直接强转，`as?`强转判断
* `init`方法代替java中的{}

## 单例
使用`object`实现单例和静态类,匿名类
```kotlin
//单例
object DataManager{

}
```

```kotlin
//静态类
class DataManager{
    //Object实现
    object Print{
       fun print(){
           print("world")
       }
    }

    //使用companion实现,推荐类内方法使用
    companion object{
       fun print(){
           print("world")
       }
    }
}
```

```kotlin
//top-level实现静态类，推荐工具类使用
fun myPrint() = print("world")
}
class DataManager {
    fun cout() {
        myPrint()
    }
}
```

## 可见修饰符
`public`：公开，可见性最大，哪里都可以引用。
`private`：私有，可见性最小，根据声明位置不同可分为类中可见和文件中可见。
`protected`：保护，相当于 private + 子类可见。
`internal`：内部，仅对 module 内可见。相比 Java 少了一个 default 「包内可见」修饰符，多了一个internal「module 内可见」修饰符。

## 关键字

* `switch`->`when`