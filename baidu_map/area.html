<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>获取地区轮廓线</title>
    <script type="text/javascript"
            src="http://api.map.baidu.com/api?v=2.0&ak=uzMdOehOj94huBKKo2bCZv8V7Ebx3HU3"></script>
    <style type="text/css">
        body {
            font-size: 13px;
            margin: 10px
        }

        #container {
            width: 800px;
            height: 500px;
            border: 1px solid gray
        }
    </style>
</head>
<body>
<div id="container"></div>
<br/>
<input type="button" onclick="test()" value="获取轮廓线">


<div id="demo" class="citys">

    <div class="layui-input-inline">
        <select class="layui-select" name="province"></select>
        <select class="layui-select" name="city"></select>
        <select class="layui-select" id="area" name="area"></select>
    </div>
</div>

<textarea id="text"
          style=" width: 1000px; height: 800px; border: 1px solid red; position: absolute; right: 0; top: 0;"></textarea>


<script type="text/javascript" src="./js/pcasunzips.js"></script>
<script type="text/javascript" src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.js"></script>

<script type="text/javascript">

    var map = new BMap.Map("container");
    map.centerAndZoom(new BMap.Point(116.403765, 39.914850), 5);
    map.addControl(new BMap.NavigationControl({type: BMAP_NAVIGATION_CONTROL_SMALL}));
    map.enableScrollWheelZoom();


    var localSearch = new BMap.LocalSearch(map);
    localSearch.enableAutoViewport(); //允许自动调节窗体大小


    function getBoundary(name) {
        var bdary = new BMap.Boundary();

        // name = $("#area").val();


        bdary.get(name, function (rs) {       //获取行政区域

            // map.clearOverlays();        //清除地图覆盖物

            str = '';

            var count = rs.boundaries.length; //行政区域的点有多少个
            for (var i = 0; i < count; i++) {

                if (i % 2 == 0) {

                    f = i - 1 == -1 ? rs.boundaries[0] : rs.boundaries[i - 1];

                    str += f + ',' + rs.boundaries[i] + ';';

                }

                var ply = new BMap.Polygon(rs.boundaries[i], {strokeWeight: 2, strokeColor: "#ff0000"}); //建立多边形覆盖物
                map.addOverlay(ply);  //添加覆盖物
                map.setViewport(ply.getPath());    //调整视野
            }


            json = JSON.stringify({
                position_border: $.trim(rs.boundaries[0]),
                name: name,
                house_count: 0,
                id: 1,
                longitude: 0,
                latitude: 0
            });

            val = $("#text").val();
            (val == '') ? $("#text").val(json) : $("#text").val(val + ',' + json);


            /* localSearch.setSearchCompleteCallback(function (searchResult) {
             var poi = searchResult.getPoi(0);

             value = poi.point.lng + "," + poi.point.lat; //获取经度和纬度，将结果显示在文本框中

             console.log(value);

             json.longitude = poi.point.lng;
             json.longitude = poi.point.lat;

             json = JSON.stringify(json);

             val = $("#text").val();
             (val == '') ? $("#text").val(json) : $("#text").val(val + ',' + json);

             });*/
            localSearch.search(name);


        });

    }


    new PCAS('province', 'city', 'area', '广东省', '广州市', '荔湾区');


    function test() {

        getBoundary('南沙区');
        return;


        $("#area option").each(function (i, v) {

            name = $(v).val();
            getBoundary(name);
            return;
        })
    }


</script>
</body>
</html>