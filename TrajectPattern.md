# 从轨迹中分析人群移动模式
## 1、对轨迹进行预处理并白描
* 将数据聚合成为“停留点+起始时间+终止时间”的形式。
![image](https://user-images.githubusercontent.com/33551862/168241379-781b189e-0ae4-417c-b51e-2fc5847a00cc.png)
* 展示区域的地理位置和城市特征。观察时间范围内不同城市的流量变化，计算均值-最大值-最小值，并对异常值进行分析
![image](https://user-images.githubusercontent.com/33551862/168242073-bd33b3e0-a700-4cd5-afee-a19b9d053072.png)
## 2、挖掘轨迹中的特征（低级特征LMIs）
* N_day:某一游客在城市中停留的总天数
* S    :考虑到一个游客可能在一天中任何时间进入/离开城市，S记为第一次活动的开始时间到最后一次活动的结束时间的间隔，比N_day更精确
* R_g  :移动半径，l_c是轨迹中心的坐标

![image](https://user-images.githubusercontent.com/33551862/168244891-f51eb6f0-b60c-45cc-b255-74ea6eb12be7.png)
* D    :轨迹的直径，轨迹上两点的最远距离
## 3、对数据再一次继续预处理
  *
  *
