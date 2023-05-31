# awtk-widget-number-label

number_label 控件。用于显示数值的文本控件。

![](docs/images/ui.jpg)

## 准备

1. 获取 awtk 并编译

```
git clone https://github.com/zlgopen/awtk.git
cd awtk; scons; cd -
```

2. 获取 awtk-widget-number-label

```
git clone https://github.com/zlgopen/awtk-widget-number-label.git
cd awtk-widget-number-label
```

## 运行

1. 生成示例代码的资源

```
python scripts/update_res.py all
```
> 也可以使用 Designer 打开项目，之后点击 “打包” 按钮进行生成；
> 如果资源发生修改，则需要重新生成资源。

如果 PIL 没有安装，执行上述脚本可能会出现如下错误：
```cmd
Traceback (most recent call last):
...
ModuleNotFoundError: No module named 'PIL'
```
请用 pip 安装：
```cmd
pip install Pillow
```

2. 编译

* 编译 PC 版本

```
scons
```

* 编译 LINUX FB 版本

```
scons LINUX_FB=true
```

> 完整编译选项请参考 [编译选项](https://github.com/zlgopen/awtk-widget-generator/blob/master/docs/build_options.md)

3. 运行

```
./bin/demo
```

## 如何使用 number-label 控件

在 xml 文件中创建 number-label 控件

```xml
<number_label name="number_label" x="c" y="m" w="100" h="50" value="200.2" format="%.2lf" decimal_font_size_scale="0.5"/>
```

number_label 各属性的功能如下表所示：

| 属性名                  | 作用                                         |
| ----------------------- | -------------------------------------------- |
| value                   | 数值                                         |
| format                  | 格式化显示的值                               |
| decimal_font_size_scale | 小数部分字体大小与整数部分字体大小之比       |
| min                     | 最小值                                       |
| max                     | 最大值                                       |
| step                    | 步长，用于上下键修改时，一次增加或减少的数值 |
| loop                    | 用上下键修改时，值是否循环                   |
| readonly                | 编辑器是否只读                               |

如果需要修改字体大小或颜色，可以通过修改 `font_size` 和 `text_color` 样式来修改。

**注意事项**

当 readonly 属性不为 true 时，可以用方向键修改控件的值。如果同时使用方向键切换焦点，会存在焦点进入本控件后无法出来的问题。为了避免这个问题，可以采用以下几种措施之一：

* readonly 设置为 true
* 把按键事件重新映射。请参考 [键值映射](https://github.com/zlgopen/awtk/blob/master/docs/map_key.md)。
* 使用极简键盘。请参考 [支持极简键盘](https://github.com/zlgopen/awtk/blob/master/docs/how_to_support_5keys_3keys.md)。

## 文档

[完善自定义控件](https://github.com/zlgopen/awtk-widget-generator/blob/master/docs/improve_generated_widget.md)