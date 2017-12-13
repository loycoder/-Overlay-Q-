##[JS版]基于百度地图的 Overlay 扩展，仿Q房网实现自定义覆盖物

经常看到各大找房系统平台上，有类似这样的功能： 地图上显示当前城市的区，鼠标悬停上去，显示这个区的不规则的范围覆盖物。点击这个地区热点，显示这个地区下的详细 热点。 最近做项目也需要用到类似效果，找不到合适的，自己动手撸了一个，有需要的朋友可以做下参考。

 老规则，先上效果图：
 ![显示区域覆盖物](http://img.blog.csdn.net/20171006173851827?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMjQyMzU1Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

点击区域后显示：
![这里写图片描述](http://img.blog.csdn.net/20171006173931965?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMjQyMzU1Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

 
####大概说下实现思路：
   主要使用到 百度的 [Overlay](http://developer.baidu.com/map/reference/index.php?title=Class:%E8%A6%86%E7%9B%96%E7%89%A9%E7%B1%BB/Overlay)类。但是该类只有基本的功能，并不能满足我们的需求， 这就需要我们自己扩展了(prototype)。
    
     1.定义自己的覆盖物实体，
```
 function ComplexCustomOverlay(lon, lat, text,  index, type, id) {
        this._point = new BMap.Point(lon, lat);
        this._lon = lon;
        this._lat = lat;
        this._text = text;
        this._index = index;
        this._type = type;
        this._id = id;
    }
```
     2.继承API的BMap.Overla     
```
ComplexCustomOverlay.prototype = new BMap.Overlay();
```


	3.重写初始化自定义覆盖物构造

```
ComplexCustomOverlay.prototype.initialize = function (map) {
		//do something... （此处主要做样式的调整、事件的绑定等）
	}
```

	4.重写draw （注：此方法不是必须重写，看项目需求）

```
 ComplexCustomOverlay.prototype.draw = function () {
        var map = this._map;
        // 根据地理坐标转换为像素坐标，并设置给容器
        var pixel = map.pointToOverlayPixel(this._point);
        this._div.style.left = pixel.x - 50 + "px";
        this._div.style.top = pixel.y - 30 + "px";
    }
```
     5.最有一步，添加到地图展     
```
var polygon1 = []; //一级覆盖物存储的多边形区域
    var myOverlay1 = [];  //一级覆盖物热点

    function addFirstOverlay() {

        //存放所有的行政区级圆形覆盖物
        for (var i = 0; i < district.length; i++) {

            //添加行政区多边形覆盖物
            polygon1[i] = new BMap.Polygon(district[i].position_border, {
                strokeColor: "#31C14D",
                strokeWeight: 4,
                strokeOpacity: 0.7
            });

            //创建多边形
            mp.addOverlay(polygon1[i]);

            polygon1[i].hide();

            //添加行政区圆形覆盖物
            myOverlay1[i] = new ComplexCustomOverlay(district[i].longitude, district[i].latitude, district[i].name, district[i].house_count, i, 1, district[i].id);
            mp.addOverlay(myOverlay1[i]);
        }
    }
```

关于多边形覆盖物的生成 ,请参考百度API Boundary类。 
好了，以上是添加多边形覆盖物的步骤，其他热点就简单很多了

