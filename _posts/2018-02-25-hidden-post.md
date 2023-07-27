---
title: "Hidden Post"
hidden: true
last_modified_at:
---

This post has YAML Front Matter of `hidden: true` and should not appear in `paginator.posts`.

一. 引言

A fragment is simply a **reusable** piece of your app's user interface. Like activities, fragments have a lifecycle and can respond to user input. A fragment is always contained within the **view hierarchy of an activity** when it is shown onscreen. Due to their emphasis on reusability and modularity, it's even possible for **multiple fragments** to be hosted simultaneously by **a single activity**. **Each fragment manages its own separate lifecycle.**

Fragment 是一个简单且可重用的组件，与 Activity 类似，其拥有自己的生命周期以及响应用户的操作。当其出现在屏幕上时，Fragment 总是包含在 Activity 所对应的视图 View 的层次当中。一般情况下，一个 Activity 可以同时托管多个 Fragment ，每个 Fragment 单独管理自己的生命周期。

## 二. Fragment 生命周期

 Fragment 的生命周期有5个状态，在 *[Lifecycle.State](https://developer.android.com/reference/kotlin/androidx/lifecycle/Lifecycle.State)* API 中可以找到*。*

- **INITIALIZED**: 表示 Fragment 实例已经被初始化。
- **CREATED**: 在这个状态下，与 Fragment相关的视图 View 也会被创建。
- **STARTED**: 该状态表示 Fragment 在屏幕上**可见**，但是并**不能对用户的操作进行响应**。
- **RESUMED**: Fragment 可见并且能够响应用户的操作。
- **DESTROYED**: Fragment 对象被销毁。

 与 Activity 类似，Fragment 也提供了与生命周期所对应的方法。

- **`onCreate()`**: Fragment 已经被初始化并且进入**`CREATED`**，但是其多对应的 View 还没有被创建。
- **`onCreateView()`**: 该方法的用途是渲染布局，同时该 Fragment 已经进入了**`CREATED`**。
- **`onViewCreated()`**: View 被创建之后会调用该方法，该方法中一般是进行与 View 相关的操作，如**`findViewById()`**。
- **`onStart()`****:** Fragment 进入**`STARTED`** 。
- **`onResume()`**: Fragment 进入 **`RESUMED`** ，同时可以响应用户的操作。
- **`onPause()`**: Fragment 重新进入**`STARTED`** ，UI 对用户而言是可见的。
- **`onStop()`**: Fragment 重新进入**`CREATED`** ，对象已经被初始化但是不再出现在屏幕上。
- **`onDestroyView()`**: 在 Fragment 进入**`DESTROYED`** 之前立即调用。视图 View 已经从内存中移除，但是 Fragment 对象仍然存在。
- **`onDestroy()`**:  Fragment 进入**`DESTROYED`** 。
