# canvas常用API
## 形状

> 矩形

* ctx.fillRect()  填充矩形
* ctx.strokeRect() 框线矩形

> 圆

* ctx.arc()  圆
* ctx.arcTo() 圆弧

> 线

* ctx.beginPath() 开始一个路径
* ctx.moveTo()    将一个新的子路径的起始点移动到 (x，y) 坐标
* ctx.lineTo()    
  让路径中`拥有`(并不会直接绘制)一条到某点的线
* ctx.rect()
  让路径中`拥有`(并不会直接绘制) 一个矩形
* ctx.fill()      填充当前路径
* ctx.stroke()    描边当前路径
* ctx.closePath() 结束一个路径

// 从画布中清除矩形区域
// 画布的特点，绘制上的元素无法更改
* ctx.clearRect()

* ctx.quadraticCurveTo(cp1x,cp1y,x,y)  二次贝塞尔
* ctx.bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)  三次贝塞尔

## 位移(挪动画布)
只保存画布(包含画笔)`状态`
ctx.save()
ctx.restore()

ctx.translate()
ctx.rotate()
ctx.scale()

// 清理画布的两种方式
document.onclick(function(){
  canvas.width = canvas.height = 600;
  ctx.clearRect(0,0,600,600)
  })

##　样式
* ctx.fillStyle = 'rgba(0,0,0,0.8)';  设置图形的填充颜色
* ctx.strokeStyle = '#1b2888';     设置图形轮廓的颜色
* ctx.globalAlpha = 0.4     设置图片的透明度

* ctx.lineWidth         设置线条宽度(给设定的值加上0.5就不会出现不清楚的情况)
* ctx.lineCap           设置线条末端样式
* ctx.lineJoin          设定线条与线条间接合处的样式
* ctx.miterlimit        限制当两条线相交时交接处最大长度
* ctx.lineDashoffset    设置虚线样式的起始偏移量
* ctx.getLineDash()     返回一个包含当前虚线样式，长度为非负偶数的数组
* ctx.setLineDash()     设置当前虚线样式
### 渐变  
* ctx.createLinearGradient(x1,y1,x2,y2)  
  接受 4 个参数，表示渐变的起点 (x1,y1) 与终点 (x2,y2)
* ctx.createRadialGradient()
  接受 6 个参数，前三个定义一个以 (x1,y1) 为原点，半径为 r1 的圆，后三个参数则定义另一个以 (x2,y2) 为原点，半径为 r2 的圆

* createPattern(image, type)  
  Image 可以是一个 Image 对象的引用，或者另一个 canvas 对象。Type 必须是下面的字符串值之一：repeat，repeat-x，repeat-y 和 no-repeat

## 阴影
* shadowOffsetX = 2  设定阴影在 X 轴的延伸距离
* shadowOffsetY = 2  设定阴影在 Y 轴的延伸距离
* shadowBlur = 2   设定阴影的模糊程度
* shadowColor = "rgba(0, 0, 0, 0.5)"  设定阴影颜色效果  

## 字体文字
ctx.font = '48px san_serif';
ctx.textAlign = 'right';

ctx.fillText("aabb",0,0,300);
ctx.strokeText("aabb",0,0)

ctx.textAlign = 'center';  文本对齐选项
ctx.textBaseline = 'middle';  基线对齐选项

## 插入图片
<img>
window.onload = function(){
  var img = document.querySelector('#img');
  var xxx = ctx.createPattern(img,'no-repeat')
  ctx.fillStyle = xxx
}
var img = new Image();
img.src = 'a.png';
img.onload = function(){
  var xxx = ctx.createPattern(img,'no-repeat');
  ctx.fillStyle = xxx;
}

canvas.toDataUrl
