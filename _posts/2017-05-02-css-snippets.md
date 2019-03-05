---
layout: post
title: css代码片段
keywords: css代码片段
description: css代码片段
category: snippets
---


### 连续旋转
```
.rotate {animation: rotation 20s infinite linear;}
@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(359deg);
  }
}
```