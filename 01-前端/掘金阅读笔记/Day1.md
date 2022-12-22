# 前言

# 前置知识
鼠标点击事件
- mousedown 点击按下
- mousemove 点击按下时移动
- mouseup 点击释放
点击事件中的 event 事件参数
- clientX x位置
- clientY y位置
- offsetX x偏移量
- offsetY y偏移量

# 设计思想
当点击按下的时候
1. 克隆绝对定位元素
2. 记录初始坐标
3. 标识"拖拽中"状态
点击释放时候
1. 判断是否在目标区域
2. 在区域,则 (当前偏移量 - 初始坐标 = 目标位置)