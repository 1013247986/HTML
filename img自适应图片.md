#### 考虑屏幕 dpr -- 响应式图片

正常情况下，图片的展示应该没有什么问题了。但是对于有图片可展示的情况下，我们还可以做的更好。

在移动端或者一些高清的 PC 屏幕（苹果的 MAC Book），屏幕的 dpr 可能大于 1。这种时候，我们可能还需要考虑利用多倍图去适配不同 dpr 的屏幕。

正好，`<img>` 标签是有提供相应的属性 `srcset` 让我们进行操作的。

```html

<img src='photo@1x.png'
   srcset='photo@1x.png 1x,
           photo@2x.png 2x,
           photo@3x.png 3x' 
/>
```

当然，这是比较旧的写法，`srcset` 新增了新的 w 宽度描述符，需要配合 `sizes` 一起使用，所以更好的写法是：

```html
<img 
        src = "logo.png" 
        sizes = “(min-width: 1200px) 800px, 600px" 
        srcset = “logo@1x.png 600w,
                       logo@2x.png 1200w,
                       logo@3x.png 1600w,
>
```

利用 `srcset`，我们可以给不同 dpr 的屏幕，提供最适合的图片。

**`srcset`代表：**

600px宽以下显示`logo.png`

600px宽以上显示`logo@1x.png`

1200px宽以上显示`logo@2x.png`

1600px宽以上显示`logo@3x.png`

**`sizes`代表：**

大于1200px宽度图片尺寸以800px显示

小于1200px宽度图片尺寸以600px显示