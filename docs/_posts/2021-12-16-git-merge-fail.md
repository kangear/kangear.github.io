---
layout: post
title:  "处理完git冲突不要加-m"
date:   2021-12-16 10:44:05 +0800
categories: git
typora-copy-images-to: ../assets
typora-root-url: ../
---

处理完git冲突不要加-m   

冲突是在`pull`产生的，`pull`内部自动包含了三步：`fetch`、`merge`、`commit`。冲突了，就是死在了第二步。解决完再送上一程（`git commit`）就可以了，-m信息已经准备好了("`Merge branch 'master' of xxx into branchName`")。 很像卡丁车跑着撞到墙上，工作人员把其弄好，回到正道上继续开即可。   

同事自己加了-m内容为“`解决了合并代码冲突`”，这是一个多么低级的行为。更低级的是接着说“`冲突解决完了pull不到东西`”，我tm都要吐血了，解决冲突就是pull步骤的一部分。就好比任务是杀人，杀完了突然告诉我“杀不了了，他没气了”。   

更有甚者，解决git冲突时看到IDE报红各种焦虑，git管理代码和IDE严格是两个事，报红让他报去，特别是多个module的情况下。这好比纸币某种意义下就是纸一样。   
