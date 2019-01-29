---
layout:     post
title:      "Observer&&Publish-Subscribe"
subtitle:   "essay"
date:       2019-01-29 13:00:00
author:     "upeartaker"
header-img: "img/post-bg-js-version.jpg"
header-mask: 0.3
catalog:    true
tags:
    - Design
    - Pattern
---

> Just a simple Design-Pattern

## Observer

**观察者模式本质上是一种对象行为模式，而 发布/订阅模式本质上是一种架构模式，强调组件的作用。** 

意图：定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。
动机：将一个系统分割成一系列相互协作的类有一个副作用：需要维护相关对象间的一致性。不希望为了维持一致性而使各类紧密耦合，这样会降低可重用性。

**example**

```javascript
function Subject () {
			this.observers = new ObserverList()
		}
		// prototype foo for add observer
		Subject.prototype.addObserver = function(observer){
			return this.observers.add(observer)
		}
		Subject.prototype.removeObserver = (observer)=>{
			return this.observers.remove(observer)
		}
		Subject.prototype.notify = ()=>{
			this.observerList.forEach(v => {
				v.update()
			})
		}


		// create observerList 
		function ObserverList () {
			this.obverserList = []
		}
		ObverserList.prototype.add = function (observer) {
			return this.ObverserList.push(observer)
		}
		ObserverList.prototype.remove = (observer)=>{
			let _i = this.observerList.indexOf(observer)
			return this.ObserverList.splice(_i,1)
		}

		// create observer
		function Observer () {
			
		}
		Observer.prototype.update = ()=>{
			
		}

		// extend obj 给一个对象扩展成主题   extend(newOBj,new Subject())
		function extend (obj,extension){
			for(let key in extension){
				obj[key] = extension[key]
			}
		}
```



## publish-subscribe

发布/订阅模式使用位于希望接收通知的对象（订阅者）和发起事件的对象（发布者）之间的主题/事件频道。这个事件系统允许代码定义特定于应用程序的事件，这些事件可以传递包含订户所需值的自定义参数 这里的想法是避免用户和发布者之间的依赖关系。 这里和观察者模式就不一样了。侧重点在于订阅者订阅事件，发布者发布信息，至于订阅者接受信息之后的处理并不关心。但是这个地方的问题在于Subject已经是项目的一个实实在在的构成部分，它不再是一个去规范行为的东西。这也是为什么一开始说是一种架构模式。 

**example**

```javascript
eventBus
```



## The difference between the two 

### 主题与订阅者之间的联系

观察者模式是一种紧耦合的状态，而发布/订阅模式是一种松耦合的状态。 

### 通知订阅者的方式

观察者模式是通过主题自己本身去遍历观察者，然后调用订阅者的通知方法去实现的。而发布/订阅模式是通过事件管道去通知的，其实做这个事情的主题是是事件，因为在执行具体的事件的时候 ，没人知道接下来执行的方法是什么吗？因为订阅/发布模式维护了所有的订阅者事件。其实二者之间就好像一个是授之以渔，另外一个是授之以鱼。 

观察者模式告诉我们接下来代码运行的步骤，而订阅/发布模式就好像是自己亲自上阵将所有的事情搞好。 

### 内部维护的内容

观察者模式维护了观察者，知道有哪些观察者在关注。订阅/发布模式则省略了这一步骤，直接维护订阅者的事件机制，直接执行具体的事件好了，至于是谁在订阅，管他的呢！ 