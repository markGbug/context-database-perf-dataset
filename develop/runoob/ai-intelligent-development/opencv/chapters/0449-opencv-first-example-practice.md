# OpenCV：OpenCV 入门实例

- 来源：[OpenCV 入门实例](https://www.runoob.com/opencv/opencv-first-example.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCV 入门实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
