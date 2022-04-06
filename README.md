# 云开发情侣互动小程序（做任务，攒积分，换商品）

这是使用云开发能力构建的情侣互动小程序，可以跟女朋友互动哦，其中使用了云开发三大基础能力的使用：
- 数据库：对文档型数据库进行读写
- 文件存储：在小程序前端直接上传/下载云端文件，在云开发控制台可视化管理
- 云函数：在云端运行的代码，微信私有协议天然鉴权，开发者只需编写业务逻辑代码
  
## 部署方式
- 在左上角点击【云开发】按钮，进入云开发控制台。
- 如果没有环境则按照提示开通云开发环境
- 进入云开发环境，在【设置】页复制`环境ID`
- 将 `miniprogram/envList.js` 文件里的内容全部替换成如下，注意替换envId
``` js
module.exports = {
  envList: [{
    envId:'上述步骤中你获得的环境ID'
  }]
}
```

- 在控制台数据库页，创建云开发数据库集合 'MarketList'， 'MissionList' 和 'UserList':在这个集合里面创建两个数据，里面创建两个值：_openid(string类), credit(number类)，credit设置为零 。（openid具体数据稍后再填）
- 选择云开发里数据库三个选项中的最后一个 数据权限，选择自定义，然后点击新窗口下面蓝色加亮文字，这个时候文本框里面应该已经写好了两行，把那个没有设置为true的也设置为true。接下来重复此步骤 把剩下两个数据集合的权限也设置好。（没有设置会导致你们互相看不到彼此发的任务和商品，也无法赚积分）
- 右键点击 `cloudfunctions/getOpenId` 文件夹，选择云函数云端安装依赖上传
- 然后创建体验版小程序 分享到女朋友手机上 具体方法要先登录微信公众平台官网
- 在两个手机上运行小程序 分别在两个手机上的小程序里新建任务 然后回到missionlist数据库集合去找自己和女朋友的_openid变量
- 把这两个openid拷贝到UserList数据集合里刚刚创建的的_openid变量中 同时也要把他们拷到app.js里的kirbyOpenId和deeOpenId的值里（kirbyOpenId是星之卡比，deeOpenId是瓦豆鲁迪）
- 然后再试试看是不是成功了！不行就问我。（右滑任务或商品可以删除或者星标哦）

## 效果
![alt text](https://github.com/UxxHans/Rainbow-Cats-Personal-WeChat-MiniProgram/blob/main/Pictures/main.jpg)
