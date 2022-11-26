Matplotlib Note
===============

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

plt.title("title")#括号当中输入标题的名称
plt.rcParams['font.sans-serif']=['SimHei']
plt.rcParams['axes.unicode_minus']=False
plt.figure(figsize=(6, 3))
plt.plot(6, 3)
plt.plot(3, 3 * 2)
plt.show()

plt.xlim(0,6) #x轴坐标轴
plt.ylim((0, 3))#y轴坐标轴
plt.xlabel('X')#x轴标签
plt.ylabel('Y')#y轴标签
plt.show()

plt.plot(2, 3, label="123")#第一个label
plt.plot(2, 3\* 2, label="456")#第二个label
plt.legend(loc='best')#图列位置，可选best，center等
plt.show()

x=np.linspace(0,10,200)#从0到10之间等距产生200个值
y=np.sin(x)
plt.plot(x,y,linestyle=':',color='b')
plt.annotate(s='标记点',xy=(3,np.sin(3)),xytext=(4,-0.5),weight='bold',color='b',\arrowprops=dict(arrowstyle='-|>',color='k'))
   # s: 注释信息内容
   # xy:箭头点所在的坐标位置
   # xytext:注释内容的坐标位置
   # arrowprops：设置指向箭头的参数
plt.show()

# 柱状图
plt.bar(x, y)
df = pd.DataFrame(np.random.rand(10, 3), columns = ['a', 'b', 'c'])
df.plot(kind = 'bar'， grid = True, colormap = 'summer_r')
df.plot(kind = 'bar',  grid = True, colormap = 'Blues_r', stacked = True) # 多系列堆叠图
df.plot.barh( grid = True, colormap = 'BuGn_r') # 水平向


# 散点图
plt.scatter(x,y)
plt.scatter(x, y,s, c=colors, alpha=0.5)

df = pd.DataFrame(np.random.randn(100, 4), columns = list('abcd'))
pd.scatter_matrix(df, figsize = (8,6),marker = 'o',diagonal = 'kde',alpha = 0.4,range_padding = 0.05)


# 饼图
plt.pie(x)
plt.pie(sizes,labels=labels,autopct='%1.1f%%',shadow=False,startangle=100)

# 直方图

s = pd.Series(np.random.randn(1000))
s.hist(bins = 20,histtype = 'bar',align = 'mid',orientation = 'vertical',alpha = 0.5,normed = True)
s.plot(kind = 'kde', style = 'k--')

df = pd.DataFrame({'a':np.random.randn(500) + 1, 'b':np.random.randn(500), 'c':np.random.randn(500) - 1, 'd':np.random.randn(500)}, columns = list('abcd'))
df.plot.hist(stacked = True,bins = 10,colormap = 'Blues_r',alpha = 0.5,grid = True)

# 极坐标图
plt.subplot(121, projection='polar')


###极区图
N = 20
theta = np.linspace(0, 2 * np.pi, N, endpoint = False)
radii = 10 * np.random.rand(N)
width = np.pi / 4 * np.random.rand(N)

ax = plt.subplot(111, projection = 'polar')
bars = ax.bar(theta, radii, width = width, bottom = 0.0)

# 箱型图
np.random.seed(100)#生成随机数
data=np.random.normal(size=1000,loc=0,scale=1)
plt.boxplot(data,sym='o',whis=1.5)

data=np.random.normal(size=(1000,4),loc=0,scale=1) #1000个值得4维数组
lables = ['A','B','C','D']
plt.boxplot(data,labels=lables)

# 热图
X = [[1,2],[3,4],[5,6]]
plt.imshow(X)
plt.colorbar()


# Reference
b:blue
g:green
r:red
c:cyan
m:magenta
y:yellow
k:black
w:white

plt.plot(y,'-') #实线
plt.plot(y+1,'--')#虚线
plt.plot(y+2,'-.')#点划线
plt.plot(y+3,':')#点线

plt.plot(y,'o') #圆点
plt.plot(y+0,'x') #叉点
plt.plot(y+1,'D') #菱形点
plt.plot(y+2,'^') #三角点
plt.plot(y+3,'p') #五边形点

