---
title: 瞄准星指令
weight: 270
---

# 关于瞄准星

瞄准星模仿了 CS:GO 中的瞄准星，因此任何现有的 CS:GO 瞄准星配置都可以在 FiveM 中使用。

*预设瞄准星的示例：*

```
cl_customcrosshair 1;cl_crosshairstyle 5;cl_crosshairsize 3.5;cl_crosshair_drawoutline 1;cl_crosshairthickness 1;cl_crosshair_outlinethickness 0.4;cl_crosshairdot 0;cl_crosshairgap -1
```

*CS:GO 的现有文档：* https://counterstrike.fandom.com/wiki/Crosshair

# 控制台变量：

### cl_customCrosshair \<bool\>
切换自定义准星。

示例： `cl_customCrosshair <true|false>`

### cl_crosshairdot \<bool\>
控制准星中心点是否可见。

示例： `cl_crosshairdot <true|false>`

### cl_crosshairsize \<float\>
控制瞄准星的长度。

示例： `cl_crosshairsize 5.0`

### cl_crosshairstyle \<int\>
控制瞄准星的样式。

示例： `cl_crosshairstyle 0`

### cl_crosshairthickness \<float\>
控制瞄准星的中心点和线的粗细。

示例： `cl_crosshairthickness 0.5`

### cl_crosshairgap \<float\>
控制十字中心的中心点和线条之间的间隙。

示例： `cl_crosshairgap 1.0`

### cl_crosshair_drawoutline \<bool\>
控制瞄准星是否应具有轮廓。与`cl_crosshair_outlinethickness`结合使用。

示例： `cl_crosshair_drawoutline <true|false>`

### cl_crosshair_outlinethickness \<float\>
控制瞄准星轮廓的粗细。

示例： `cl_crosshair_outlinethickness 1.0`

### cl_crosshaircolor \<int\>
范围从`0`到`5`，如果你想使用自定义瞄准星颜色(通过`cl_crosshaircolor_r`, `cl_crosshaircolor_g`, `cl_crosshaircolor_b`应用的那些)请将其设置为`5`。

#### 可用的颜色预设：
0. 红色
1. 绿色
2. 黄色
3. 紫蓝色
4. 青色/绿松石色
5. 自定义颜色 (通过`cl_crosshaircolor_r`, `cl_crosshaircolor_g`, `cl_crosshaircolor_b`应用的那些) 

示例： `cl_crosshaircolor 1`

### cl_crosshaircolor_r \<int\>
控制瞄准星的 RGB 颜色值中的红色分量。

示例： `cl_crosshaircolor_r 50`

### cl_crosshaircolor_g \<int\>
控制瞄准星的 RGB 颜色值中的绿色分量。

示例： `cl_crosshaircolor_g 250`

### cl_crosshaircolor_b \<int\>
控制瞄准星的 RGB 颜色值中的蓝色分量。

示例： `cl_crosshaircolor_b 50`

### cl_crosshairusealpha \<bool\>
控制瞄准星的透明度。与`cl_crosshairalpha`结合使用。

将此命令设置为`false`会将十字准线的 alpha 设置为`200`，使其几乎不透明。如果您想通过`cl_crosshairalpha`使用自定义透明度值，请设置为`true`。

示例： `cl_crosshairusealpha <true|false>`

### cl_crosshairalpha \<int\>
控制瞄准星的透明度。有效值从`0`到`255`。

示例： `cl_crosshairalpha 200`

### cl_crosshair_dynamic_splitdist \<float\>
未使用，控制移动或射击时瞄准星中心的扩散距离。

示例： `cl_crosshair_dynamic_splitdist 7.0`

### cl_crosshair_dynamic_splitalpha_innermod \<float\>
未使用，控制移动或射击时准星线内部的透明度。

示例： `cl_crosshair_dynamic_splitalpha_innermod 1.0`

### cl_crosshair_dynamic_splitalpha_outermod \<float\>
未使用，控制移动或射击时瞄准星外侧部分的透明度。

示例： `cl_crosshair_dynamic_splitalpha_outermod 0.5`

### cl_crosshair_dynamic_maxdist_splitratio \<float\>
未使用，控制移动或射击时瞄准星的内部和外部有多长。

示例： `cl_crosshair_dynamic_maxdist_splitratio 0.35`
