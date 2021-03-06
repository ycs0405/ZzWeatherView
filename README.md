# ZzWeatherView


一个现实天气的控件


## Gradle

```
compile 'me.zhouzhuo.zzweatherview:zz-weather-view:1.0.1'
```


效果图如下：

<img src="https://github.com/zhouzhuo810/ZzWeatherView/blob/master/zz-weather-view-demo.jpg"  width="400px"/>
<img src="https://github.com/zhouzhuo810/ZzWeatherView/blob/master/zz-weather-view-demo_disc.jpg"  width="400px"/>

## 用法简介

1）布局

### drawable/scroll_bar_thumb.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient android:startColor="#33999999" android:endColor="#80aaaaaa"
        android:angle="0"/>
    <corners android:radius="6dp" />
</shape>
```



```xml
    <me.zhouzhuo.zzweatherview.ZzWeatherView
        android:id="@+id/weather_view"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:scrollbarThumbHorizontal="@drawable/scroll_bar_thumb"
        android:scrollbarTrackHorizontal="@drawable/scroll_bar_thumb"
        android:scrollbarSize="4dp"
        android:background="#333"
        >
    </me.zhouzhuo.zzweatherview.ZzWeatherView>

```


2）java


```java
        ZzWeatherView weatherView = (ZzWeatherView) findViewById(R.id.weather_view);

        //填充天气数据
        weatherView.setList(generateData());

        //画折线
        weatherView.setLineType(ZzWeatherView.LINE_TYPE_DISCOUNT);
        //画曲线(不够圆滑希望有更好的建议联系我(Email:admin@zhouzhuo810.me))
        //weatherView.setLineType(ZzWeatherView.LINE_TYPE_CURVE);

        //设置线宽
        weatherView.setLineWidth(6f);

        //点击某一列
        weatherView.setOnWeatherItemClickListener(new ZzWeatherView.OnWeatherItemClickListener() {
            @Override
            public void onItemClick(WeatherItemView itemView, int position, WeatherModel weatherModel) {
                Toast.makeText(MainActivity.this, position+"", Toast.LENGTH_SHORT).show();
            }
        });
       
        
```

```java
    //数据源
  WeatherModel model = new WeatherModel();
        model.setDate("12/07");//日期
        model.setWeek("昨天");  //星期
        model.setDayWeather("大雪"); //白天天气
        model.setDayTemp(11); //白天温度
        model.setNightTemp(5); //夜晚温度
        model.setNightWeather("晴"); //夜晚天气
        model.setWindOrientation("西南风"); //风向
        model.setWindLevel("3级"); //
        model.setAirLevel(AirLevel.EXCELLENT); //空气质量
```
