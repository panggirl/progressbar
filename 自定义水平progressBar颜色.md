# 自定义水平progressBar颜色
Android支持几种风格的进度条，通过Style属性可以为进度条ProgressBar指定风格，该属性支持一下几个属性值。
```
@android：style/widget.ProgressBar.Horizontal————水平进度条
@android：style/widget.ProgressBar.Inverse————不断跳跃、旋转画面进度条
@android：style/widget.ProgressBar.Large————大进度条
@android：style/widget.ProgressBar.Large.Inverse————不断跳跃、旋转画面的大进度条
@android：style/widget.ProgressBar.Small————小进度条
@android：style/widget.ProgressBar.Smal.Inversel————不断跳跃、旋转画面的小进度条
```

XML属性   说明
```
android:max 设置该进度条的最大值
android:progress    设置该进度条的已完成进度值
android:progressDrawable    设置该进度条的轨道的绘制形式
android:progressBarStyle    默认进度条样式
android:progressBarStyleHorizontal  水平进度条样式
android:progressBarStyleLarge   大进度条样式
android:progressBarStyleSmall   小进度条样式
```
上表中的android:progressDrawable用于指定进度条的轨道的绘制形式，该属性可以指定一个LayerDrawable对象
（该对象可以通过在xml文件中用<layer-list>元素进行配置）的引用。

ProgressBar提供了如下方法来操作完成百分比：
-----------------------------
* `setProgress(int)`:设置进度完成百分比。
* `incrementProgressBy(int)`:设置进度条的进度增加或减少。当参数为正数时增加，反之则减少。


自定义`layer-list` ,drawable目录右键新建 layer_progress.xml 文件
------------------------------
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">

    <!-- 总进度的颜色 -->
    <item android:id="@android:id/background">
        <shape>
            <corners android:radius="@dimen/xol_revision_margin_4"/>
            <solid android:color="#55ffffff" />
        </shape>
    </item>
    <!-- 缓存的颜色 -->
    <item android:id="@android:id/secondaryProgress">
        <clip>
            <shape>
                <corners android:radius="@dimen/xol_revision_margin_4" />
                <gradient
                    android:endColor="#ffc93a"
                    android:startColor="#ff9f00"></gradient>
            </shape>
        </clip>
    </item>

    <!-- 当前进度的颜色 -->
    <item android:id="@android:id/progress">
        <clip>
            <shape>
                <corners android:radius="@dimen/xol_revision_margin_4" />
                <gradient
                    android:endColor="#ffc93a"
                    android:startColor="#ff9f00"></gradient>
            </shape>
        </clip>
    </item>
</layer-list>
```
在布局文件中是使用
```
   <ProgressBar
                android:id="@+id/pb_studied_progress"
                style="@style/Widget.AppCompat.ProgressBar.Horizontal"
                android:layout_width="match_parent"
                android:layout_height="4dp"
                android:layout_marginLeft="20dp"
                android:layout_marginTop="10dp"
                android:layout_marginRight="20dp"
                android:progressDrawable="@drawable/xol_revision_layer_progress"
       />
```


