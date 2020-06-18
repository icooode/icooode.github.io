---
title: Unity之Specified cast is not valid.报错
date: 2020-04-24 20:03
tags: Unity
category: Unity
---
Unity之Specified cast is not valid报错，原来是类型引起的锅。
<!--more-->
***Unity之Specified cast is not valid.报错***
```
foreach (Gameobject child in Instance.slotGrid.gameObject.transform)
{
    Destroy(child.gameObject);
}
```
我调试了一会儿，发现百思不得其解，就百度了下这个错误，然后大概猜出这应该是个类型导致的错误。
```
foreach (Transform child in Instance.slotGrid.gameObject.transform)
{
    Destroy(child.gameObject.gameobject);
}
```
再在Unity中运行，没有报错了！

总结：Unity 报错“Specified cast is not valid”，是类型错误。
