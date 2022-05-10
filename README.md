# TrajectGeneration
如何挖掘出人群移动模式并基于实时外部环境进行轨迹仿真
## **一些想法**
### **相关工作**
#### * 基于gan的轨迹生成
   ##### * **seqgan**
   使用gan模型进行轨迹生成
   * word_embeeding 没有捕获轨迹点本身的空间信息，更不谈移动模式了
   * 只能做到粗粒度固定时间间隔的轨迹生成，grid-grid，精度不够，可修改性差
   * 不能保证生成的轨迹整体满足区域流量的分布
   
   #####  * **movsim**
   同样是做了序列生成，不同的是在生成器部分加入了地理信息的矩阵
   * 加入了空间信息，使得整个模型从一个文本生成任务变得更像是轨迹生成任务
   * 加入了蒙特卡洛搜索进行采样，尽可能让生成轨迹的分布=真实轨迹的分布
   * 分别在距离、半径、停留时间等指标上用了生成轨迹与真实轨迹的差异，再一次强调了作者想要生成的**真实**轨迹。
   * 空间信息是用于生成器做下一点预测，如果纯粹是markov模型，由于人行为不同/时间不同，转移的概率也不尽相同，所以算是丢掉了时间信息
   * 在判别器中并没有用上空间信息
   
   ##### * **STG**
   使用两个gan来进行细粒度的生成，目标是在基于grid生成的基础上进一步的加入空间信息，进行更细粒度的生成
   * **使用了一种循序渐近的方法，将精细化轨迹生成拆分成为两个子任务，分别完成模型的训练**
   * 
   
   



















## 论文 **启示**
---
### 基于gan的轨迹生成


#### * seqgan
基于gan的序列生成模型，生成器和判别器都使用**LSTM**。使用预测任务预训练生成器，使用分类任务预训练判别器。在对抗训练的过程中引入了强化学习的**policy gradient**
![image](https://user-images.githubusercontent.com/33551862/167591398-f62d7e1f-fc36-4723-8716-6fcaf1ff85bd.png)


* movsim
