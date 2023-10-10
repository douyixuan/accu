# 数字图像处理/缩放/最近邻插值法

在计算机图形学中, 图像缩放指的是通过增加或去掉像素来改变图片的尺寸. 由于要在效率和图像质量比如平滑度和清晰度之间做折衷, 图像缩放并不是个平庸的过程. 当图像尺寸增大的时候, 组成图像的像素也越来越大, 图像看上去就变"柔和"了. 而缩小图像的时候, 图像就变得平滑和清晰了. 本文介绍最简单的最近邻插值法(Nearest-neighbor interpolation).

## 转换函数

近邻取样插值法是将目标图像各点的像素值设为原图像中与其最近的点.

## 代码实现

```py
import PIL.Image

im = PIL.Image.open('/img/jp.jpg')
im_resized = PIL.Image.new(im.mode, (480, 270))
for r in range(im_resized.size[1]):
    for c in range(im_resized.size[0]):
        rr = round((r+1) / im_resized.size[1] * im.size[1]) - 1
        cc = round((c+1) / im_resized.size[0] * im.size[0]) - 1
        im_resized.putpixel((c, r), im.getpixel((cc, rr)))
im_resized.show()
```
