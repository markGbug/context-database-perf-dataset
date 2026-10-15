# OpenCV：OpenCV 入门实例

- 来源：[OpenCV 入门实例](https://www.runoob.com/opencv/opencv-first-example.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0449

## 本章内容

接下来我们来看一个简单的 OpenCV 实例，我们将实现以下功能：

- 读取一张图像。
- 显示图像。
- 保存图像。
- 添加简单的用户交互。

可以以以下图片为例：

以下代码保存在 display_image.py 文件中：


## 实例（Python）

```text
python display_image.py
```

弹出窗口显示如下：

在显示的图像窗口中，按下 s 键保存图像，或按下其他键退出。

以上实例的 C++ 代码如下：


## 实例（C++）


### 扩展练习

接下来我们可以尝试做一些代码的修改。

1、修改窗口名称：将 "Display Image" 改为其他名称，例如 "My Image"。

```text
cv2.imshow("My Image", image)
```

2、保存为不同格式：将 "saved_image.jpg" 改为 "saved_image.png"，观察保存结果。

```text
# 4. 根据用户按键执行操作
if key == ord('s'):  # 如果按下 's' 键
    # 保存图像
    output_path = "saved_image.png"
    cv2.imwrite(output_path, image)
    print(f"图像已保存为 {output_path}")
```

3、添加更多交互：例如，按下 'q' 键直接退出程序。

```text
if key == ord('s'):  # 如果按下 's' 键
    # 保存图像
    output_path = "saved_image.jpg"
    cv2.imwrite(output_path, image)
    print(f"图像已保存为 {output_path}")
elif key == ord('q'):  # 如果按下 'q' 键
    print("程序已退出。")
else:  # 如果按下其他键
    print("图像未保存，程序已退出。")
```

- ord('q') 返回字符 'q' 的 ASCII 码值。
- 如果用户按下 'q' 键，打印提示信息 "程序已退出。"，然后程序会继续执行 cv2.destroyAllWindows() 关闭窗口并退出。


## 记忆卡片

- 一句话定义：`OpenCV 入门实例` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
