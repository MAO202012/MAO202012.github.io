---
layout: post
title: 我的问题
categories: 
description: 
keywords: 
comments: true
---

## 2020.12.17 概率图？怎么得来的
<div align="center"> 
    <img src="https://MAO202012.github.io/images/2.png" style="zoom:100%" />
    
 
</div> 
[VRNN,SRNN]（https://zhuanlan.zhihu.com/p/272106709）

## 2020.12.11 neural ode 里面 latent ode的重构误差是怎么实现的
<div align="center"> 
    <img src="https://MAO202012.github.io/images/1.png" style="zoom:100%" />
    
 
</div> 

```python
def log_normal_pdf(x, mean, logvar):
    const = torch.from_numpy(np.array([2. * np.pi])).float().to(x.device)
    const = torch.log(const)
    return -.5 * ( + logvar + (x - mean) ** 2. / torch.exp(logvar))

logpx = log_normal_pdf(
                samp_trajs, pred_x, noise_logvar).sum(-1).sum(-1)
```
[rtqichen/torchdiffeq/examples/latent ode](https://github.com/rtqichen/torchdiffeq)

## 2020.12.11 neural ode 里面最后一部分的泊松过程是怎么添加进loss的
![image-20201213175605871](https://RuifMaxx.github.io/images/12.14/16.png)

the joint distribution is defined as:

<div align="center"> 
    <img src="https://RuifMaxx.github.io/images/12.14/32.png" style="zoom:100%" />
    
 
</div> 


![image-20201213175704761](https://RuifMaxx.github.io/images/12.14/17.png)
