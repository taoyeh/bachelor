# 问题
今天在写andorid的时候发现setOnItemClickListener无响应，后面发现需要把子项当中   

`android:focusable="false"`

然后父项当中

` android:descendantFocusability="blocksDescendants""`


第一个是子项主动不接受焦点，第二个是父容器不给子控件第一响应。
