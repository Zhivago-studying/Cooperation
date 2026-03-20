# 就是MATLAB咯
## 命令行  
1. 爽爽当计算器用，ones(3,4)可以初始化数组  
2. ；分号隐藏输出，  
   %百分号注释，  
   Inf无穷大，  
   sqrt()开平方，  
   who 显示所有变量  
   \* 矩阵乘法   
   .* 按位乘
   ~= 不等于,你最好是别写"!"  
3. format long %精确到16位  
   format short e %科学计数法  
   format rat %小数转分数  
4. a = [1,2,3] a = [1 2 3] 行向量
   a = [1;2;3] 列向量

## 脚本  
1. 条件语句  
``` matlab
if expression
    statement
else 
    statement
end   %你给我记住这个end

% switch啦
switch expression
    case value1
        statement
    case value2
        statement
    otherwise
        statement
end
```
2. 循环语句  
```matlab
for index = start:step:end  %你最好是看清楚这个顺序，两边都是闭区间
    statement
end  %你最好是还没忘记这个end

%  while循环啦
while expression
    statement
end
```
3. 函数  
```matlab
function [y] = funcname(x)  
% 函数声明，y是返回变量，很无语只能返回变量，x是参数
    y = x^2;
end  %你最好记得这个end,而不是
```
4. 矩阵运算  
``` matlab
A = [1 2 3; 4 5 6; 7 8 9];
transpose_A = A';   %转置,或者transpose(A)
inv(A);             %求逆
cross(A,B);         %叉乘
dot(A,B);           %点乘
det(A);             %行列式
eye(3);             %单位矩阵
rank(A);            %秩
```
## 绘图
```matlab
close all;  %关闭所有窗口
figure;     %新建窗口
x = linspace(0,2*pi,100);   %生成100个点，从0到2pi区间等距分布
y = sin(x);     % y的函数
plot(x,y,'r--+')    % 线型图
title('wave');  % 标题
xlabel('x');    % x轴标签
ylabel('sin(x)');   % y轴标签
xlim([0 2*pi]); % 限制x轴范围
ylim([-1 1]);   % 限制y轴范围

hold on;        % 保持当前figure，只在这个图上画
hold off;       % 放弃当前figure，画新图,配对使用

legend('sin(x)','cos(x)')   % 显示图例,顺序一定要和plot的顺序一致
text(x,y,'tex')     % 显示文本,在(x,y)

%坐标区外观
box on/off      % 边框开关
grid on/off     % 网格开关
axis            % 设置坐标轴范围和横纵比
axis([xmin,xmax,ymin,ymax]) %相当于xlim,ylim
axis equal      % 设置横纵比为1:1
axis square      % 设置figure为正方形
axis tight       % 设置figure刚好为数据范围
axis vis3d        % 确保三维图形高宽比不变
axis auto         % 自动设置坐标轴范围
axis manual         % 手动设置坐标轴范围
axis ij             % 设置y轴向下为正，默认为xy
axis off           % 关闭坐标区背景，默认on
xticks([1 5 9])     % 设置显示的x轴刻度
xticklabels({'左边','中间','右边'})      % 设置x轴刻度标签，一般要先设置xticks
xtickangle()        % 设置x轴刻度标签角度,单位度

% 绘制多子图
subplot(2,1,1);        % 前两位为子图分布行列数，第三位为子图编号，顺序为从左往右，若指定第四位 [3 4],则占用两张图的位置
tiledlayout(2,1,'tilespacing','tight','padding','tight'); 
% 绘制多子图，前两位为字体分布，tilespacing设置子图间距，'loose'为松散，'tight'为紧凑，'none'为无间距,padding设置布局周围空白区域
nexttile(2,[1 2])     %绘制子图，前参数为起点，后参数为图大小，如这里是1行2列的大小。
```

## simulink

## 数学运算
``` matlab
% 拉普拉斯变换
ft = t^2+2*t+2;
Fs = laplace(ft,t,s);
%拉普拉斯变换，[1]方程，[2]方程中的自变量，[3]变换后的自变量
ft = ilaplace(Fs,s,t); 
%反变换

%解多项式方程
P = [4 3 2 1];  %系数向量
 r = roots(P);  %解

%解微分方程
syms y(t);
ode = 2*diff(y,t,2) + 3*diff(y,t) + 4*y == 0; %微分方程,注意==
Dy = diff(y,t);     %定义算子
cond = [y(0)==0,Dy(0)==1]; %初始条件
ySol = dsolve(ode,cond); %求解

%有理分式转零极点形式
num = [1 3];        %分子系数
den = [1 0 2 1];    %分母系数
dt = 2;             %延时，即exp(-2s)
g = tf(num,den);    %有理分式,若有延时，需加'inputdelay',加dt.
g = zpk(g);         %零极点形式
%%
z = [];             %零点向量
p = [];             %极点向量
k = 3;              %增益
g = zpk(z,p,k);     %零极点形式
% 部分分式展开
[r ,p ,k ] = residue(num,den)       %部分分式展开
%得到r为各项分式的系数向量，p为零点向量，k为常数
%若有多重根，则分母为升幂顺序

