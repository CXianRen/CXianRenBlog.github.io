+ 简约01
![img](img/miniprom_images/nb_01.PNG)

+ wxml
```html
<view class='tablist'>
  <view wx:for="{{tabList}}" class='item {{current==index?"select":""}}' data-pos='{{index}}' bindtap='tabItemClick'>
    <text>{{item}}</text>
  </view>
</view> 
```
+ wxss
```css
.tablist {
  display: flex;
  background: white;
  height: 60rpx;
}

.tablist .item {
  flex: auto;
  display: flex;
  position: relative;
  justify-content: center;
  align-items: center;
  font-size: 11pt;
  color: #353535;
}

.tablist .item.select {
    color: #e64340;
}

.tablist .item.select::after {
    content: "";
    height: 3rpx;
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    right: 0;
    background: #e64340;
}
```
