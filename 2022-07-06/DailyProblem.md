# IOS代码裁剪导致TimeLine动画播放显示异常。
    定位确实有问题，后面发现是Link.xml里面保留的类库名字有问题
![](2022-07-06-14-20-12.png)
    发现TimeLine主要在Unity.TimeLine的dll下面，而不是UnityEngine.TimeLine.dll下面，这个容易弄混。
![](2022-07-06-14-21-25.png)

以后要是遇到其他类似的情况，就先确认对应的类库是否都有，没有被裁减掉，比如:
![](2022-07-06-14-22-26.png)
![](2022-07-06-14-22-46.png)
先在pc端可以验证，对应的dll有没有缺失，可以通过BeyondCompare来看差异
![](2022-07-06-14-23-51.png)
已经有的就先不用动了
![](2022-07-06-14-24-17.png)
用ILSpy反编译Unity.Timeline.dll确定基本都包含了
![](2022-07-06-14-25-02.png)
再验证，基本就没什么问题了。