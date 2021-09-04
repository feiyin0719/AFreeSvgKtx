# AFreeSvgKtx

[![](https://jitpack.io/v/feiyin0719/AFreeSvgKtx.svg)](https://jitpack.io/#feiyin0719/AFreeSvgKtx)

[AFreeSvg](https://github.com/feiyin0719/AFreeSvg)的kotlin扩展库（需0.0.3以上版本支持），支持使用kotlin方便快捷的创建filter gradient shape


## 参考代码

创建filter
```kotlin
fun createFilterGroup(): SVGFilterGroup {
    return filterGroup {
        filterUnits = PosMode.MODE_BOX
        x = -0.2f
        y = -0.2f
        width = 1.5f
        height = 1.5f
        offsetFilterNode {
            `in` = SVGBaseFilter.ALPHA_VALUE
            result = "offset"
            dx = 0.05f
            dy = 0.05f
        }
        gaussianFilterNode {
            `in` = "offset"
            result = "blur"
            stdDeviationX = 3f
            stdDeviationY = 3f
        }

        blendFilterNode {
            `in` = SVGBaseFilter.GRAPHIC_VALUE
            in2 = "blur"
        }
    }
}

```
创建 shape
```kotlin

fun createClipShape(): SVGClipShape {
    return clipShape {
        shape = shapeGroup {
            path {
                oval(0.2f, 0.2f, 0.2f, 0.2f)
            }
            path {
                oval(0.6f, 0.2f, 0.2f, 0.2f)
            }
        }
        posMode = PosMode.MODE_BOX
    }
}
```
创建gradient

```kotlin
fun createLinearGradient(): SVGLinearGradient {
    return linearGradient {
        startX(0f)
        startY(0f)
        endX(1f)
        endY(0f)
        color(0xffff0000, 0f)
        color(0xff00ff00, 0.5f)
        color(0xff00eeee, 0.75f)
        color(0xff0000ff, 1f)
    }
}
```
