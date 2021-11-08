# OpenCv学习笔记

学习opencv-python时遇到的问题，在此记录。  

* 参考文件：[python的opencv文档](https://docs.opencv.org/4.5.4/d6/d00/tutorial_py_root.html)
* opencv-python版本：4.5.4
* Python版本：3.7.3



1. 图形梯度（image gradient）

   函数$f(x)$的梯度如下所示
   $$
   \frac{\partial f}{\partial x}(x)=\lim_{\Delta x\rightarrow 0}\frac{f(x+\Delta x)-f(x)}{\Delta x}
   $$
   图形梯度类似用于表示相邻像素块间的变化率。将图像看成一个二元函数$f(x,y)$（由于行和列）。由于图像是离散的值，所以$\Delta x$或$\Delta y$取1，对应$x$和$y$方向的图像梯度如下
   $$
   \frac{\partial f}{\partial x}(x,y)=f(x+1,y)-f(x,y)=gx
   $$
   
   $$
   \frac{\partial f}{\partial y}(x,y)=f(x,y+1)-f(x,y)=gy
   $$
   
   计算各像素的图形梯度后与原图像对应元素相加可用于增强图像（尤其是边界）。
   
   将$x$和$y$方向结合得如下计算方式
   $$
   M(x)=\sqrt{gx^{2}+gy^{2}}
   $$
   为避免平方和开方计算，用绝对值逼近梯度计算
   $$
   M(x)=\left | gx \right |+\left | gy \right |
   $$
   
2. 高斯平滑（Gausssian smoothing）

   普通平滑就是卷积块中所有元素相加取平均，高斯平滑赋予范围内每个元素不同权重。下面公式中左边为普通平滑，右边为高斯平滑
   $$
   \frac{1}{9}\begin{bmatrix}
   1 &1  &1 \\ 
   1 &1  &1 \\ 
   1 &1  &1 
   \end{bmatrix}vs\begin{bmatrix}
   1 &2  &1 \\ 
   5 &4  &5 \\ 
   2 &3  &2 
   \end{bmatrix}
   $$
   
