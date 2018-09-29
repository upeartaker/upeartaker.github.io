---
layout:     keynote
iframe:     "https://docs.google.com/presentation/d/1rYogA2BDVWsNv-qjtrZQ9zHpd5lfMBPtTwkotuIIrMM/edit#slide=id.g3faf6bbf6e_0_15"
---

这两天在群里因为一道题目吵得不可开交，内容如下，判断正误：

> 回流和重绘都会导致页面重新渲染，只要页面布局没有改变，就不会触发重排。对于复杂的页面操作，可以使用diaplay:none，这样只需要两次重新渲染。

其实，对于重绘、回流的文章是有很多的，我们也都知道：”引起页面布局变化，会触发回流“,否则重绘。 但是，对于很多细节性的东西，不深究就不太容易解决。比如：
* font-size的改变
* transform的变化
* position： absolute

以上这种情况又是否会触发回流呢？

针对这些，详细的关于reflow和repaint的东西就暂时不写了，群里朋友分享了一个PPT挺不错的，这里就分享下，以供学习和参考。

##### ppt需要翻墙才能正常查看。