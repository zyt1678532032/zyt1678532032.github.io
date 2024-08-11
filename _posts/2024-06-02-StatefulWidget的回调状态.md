---
title: "StatefulWidget 的回调状态"
categories:
  - Flutter
tags:
  - StatefulWidget
---

StatefulWidget 的回调状态

1. 当 StatefulWidget 第一次被插入到 WidgetTree 时

   initState() => didChangeDependencies => build()

2. 当StatefulWidget 的 State 中持有的状态发生变化时

   **const 在 StatefulWidget 中的作用**

   如果 StatefulWidget 被 const 修饰，那么此 StatefulWidget 的 ParentWidget 在调用 setState() 时，并不会触发 child widget（也就是此StatefulWidget）任何状态回调方法，const 关键字能起到优化 Flutter 应用性能的作用。

   **Key 在 StatefulWidget 中的作用**

   见下面代码，作用是切换 StateWidget，但是两个 Widget 的 key 不同，那么在这两个 Widget 进行切换的时候，依次触发的状态回调为 StateWidgetOne: initState() => didChangeDependencies => build()，StateWidgetTwo: didUpdateWidget() => build()；而当两个 key 一致时，只会触发 didUpdateWidget() => build()。

   ```dart
   Widget _isChangeWidget() {
       return isChange
           ? StateWidget(
               key: ValueKey('StateWidgetOne'),
               title: 'StateWidgetOne',
               color: Colors.red,
             )
           : StateWidget(
               key: ValueKey('StateWidgetTwo'), // ValueKey('StateWidgetOne'),
               title: 'StateWidgetTwo',
               color: Colors.green,
             );
   ```

3. 当StatefulWidget从WidgetTree中移除时 deactivate() => dispose()