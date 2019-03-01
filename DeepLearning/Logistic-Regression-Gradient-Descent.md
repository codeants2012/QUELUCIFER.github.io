例如 有两个特征x1和x2 为了计算z 我们要输入w1,w2和b 还有特征x1和x2的值 这些东西在计算图里 用来计算z z=w1x1+w2x2+b 用方框框起来 接着计算y_hat y_hat=a=sigma(z) 这是计算图里接下来的一步 

最后我们计算L(a,y) 我不再抄一遍公式了 在逻辑回归中 我们要做的就是修改参数w和b 来减少损失函数 之前讲前向传播的步骤中 讲了如何计算单个样本的损失函数 现在我们讲讲如何反向计算导数 这是一个整理后的框图 

因为我们要计算关于损失函数的导数 反向传播时 首先要做的是 计算损失函数对于a的导数 所以 在代码中 你只要用da来表示dL/da 如果你对微积分熟悉 你可以得到dL/da=-y/a+(1-y)/(1-a) 得到的方法是 通过loss的表达式 

然后如果你熟悉微积分的话 你可以计算关于变量a的导数 然后得到这个式子 但你不熟悉的话也别担心 我们会提供导数表 和其他的这门课需要的东西 所以如果你特别熟悉微积分的话 我鼓励你从之前的讲义中 

找出损失函数的方程然后试着对a求导 如果你不懂微积分也别担心 现在已经算出了da的值 是最终输出值对a的导数 你可以继续往回 可以算出dz 是python例子中起的变量名 是损失函数 对z的导数 

你可以把损失函数显式地写成a和y的函数 或者直接写L也行 可以得到dz=a-y 讲一点过程给熟悉微积分的同学 如果你不熟悉也别担心 这个dL/dz 可以被表示成dL/da乘以da/dz da/dz可以算出 是a(1-a) 

注:仅对于sigmoid函数成立 dl/da之前得到右边这个结果 所以dl/da的表达式 和da/dz的结合起来 相乘 可以得到结果是a-y 这是求解过程 这是链式法则 如果你会微积分可以自己算算 如果不会你只需要知道 dz=a-y 

我们已经替你做完了微积分 反向传播的最后一步 是反向算出你需要改变w和b多少 特别地 你可以算出L对w1的导数 通常记作dw1 它等于x1乘以dz 同样 dw2 代表你要改变w2的值 是x2乘以dz db等于dz 

所以如果你要对于一个例子进行梯度下降 你需要做如下事情 用公式算出dz 然后算出dw1 dw2 和db 然后进行更新 w1=w1-α*dw1 α代表学习速率 w2也按一样的方式更新 b=b-αdb 这是一个简单例子 一步梯度的情况 你看了 

对于一个单一的训练样本 如何计算导数 和执行逻辑回归的梯度下降 但训练一个逻辑回归模型 你不止有一个样本 而是有m个

In the for loop depicted in the video, why is there only one dw variable (i.e. no i superscripts in the for loop)?


Only the derivative of one value is relevant.


The value of dw in the code is cumulative.

正确 