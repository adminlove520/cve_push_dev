# Github-CVE-Listener

推送GitHub最新CVE EXP/POC到微信或者TG  

![](https://ondemand.bannerbear.com/signedurl/9K5qxXae32jEAGRDkj/image.jpg?modifications=W3sibmFtZSI6InJlcG8iLCJ0ZXh0IjoiS2lyYS1QZ3IgLyAqR2l0aHViLUNWRS1MaXN0ZW5lcioifSx7Im5hbWUiOiJkZXNjIiwidGV4dCI6IuaXoOmcgOacjeWKoeWZqOeahEdpdEh1YuWunuaXtua8j-a0nuWIqeeUqOW3peWFt-ebkeWQrOWZqO-8jOebruWJjeaUr-aMgeW-ruS_oS9UR-aOqOmAge-8jOS4reaWh-eJiChodHRwczovL2dpdGh1Yi5jb20vS2lyYS1QZ3IvR2l0aHViLUNWRS1MaXN0ZW5lci9ibG9iL21haW4vUkVBRE1FX1pILm1kKSJ9LHsibmFtZSI6ImF2YXRhcjUiLCJoaWRlIjp0cnVlfSx7Im5hbWUiOiJhdmF0YXI0IiwiaGlkZSI6dHJ1ZX0seyJuYW1lIjoiYXZhdGFyMyIsImhpZGUiOnRydWV9LHsibmFtZSI6ImF2YXRhcjIiLCJoaWRlIjp0cnVlfSx7Im5hbWUiOiJhdmF0YXIxIiwiaW1hZ2VfdXJsIjoiaHR0cHM6Ly9hdmF0YXJzLmdpdGh1YnVzZXJjb250ZW50LmNvbS91LzM2MTg4MDIzP3Y9NCJ9LHsibmFtZSI6ImNvbnRyaWJ1dG9ycyIsInRleHQiOiJLaXJhLVBnciJ9LHsibmFtZSI6InN0YXJzIiwidGV4dCI6IjI4In1d&s=8a38774f2cd0d8e1e22ff344bf3bf76cfd944d342b62be8ea3f2a68ae6b34d4e)

## 说明

* 使用Github Actions运行，无需拥有服务器
* 懒得自己搭的可以加入[TG频道](https://t.me/nanosec47)
* [英文版README](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/README.md)
  
  ## 使用步骤

* **准备**
  
  * **GitHub方面的准备**
    
    * fork本项目  
      登陆/新建github账号，回到本项目页面，点击右上角fork本项目的代码，  
      ![Fork](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Fork.png)  
      然后你账号下会出现一个一模一样的项目，接下来的操作均在你的这个项目下进行。
    
    * 新建github密钥    
        1）进入创建新Token[页面](https://github.com/settings/tokens/new)  
        2）设置名字为 `GH_TOKEN` , 然后勾选repo，过期时间选择永不过期，点击 `Generate token` ，最后**复制保存**生成的github密钥  
      
      > **注意！一旦离开页面下次就看不到了！**  
      
        ![Fork](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Token.png)
    
    * 新建secret    
      
      1. 依次点击页面上栏右边的 Setting -> 左栏 Secrets -> 右上 New repository secret，新建6个secret：`GH_TOKEN` `SCKEY`  `TOTAL_COUNT` `OPTION` `TG_CHAT_ID` `TG_TOKEN`
      
         > ** 注意：不需要用到的Secret项值可以不建 **     
      
      2. 填写每个Secret的值       
         
         `OPTION`填写1或2或3(1表示微信推送，2表示TG Bot推送, 3表示都推送--以满足一些特殊情况)
         
          `GH_TOKEN`填写你获得的GitHub密钥         
         
          `TOTAL_COUNT`填0     
         
         * 如推送微信 
            `SCKEY`填写你的SendKey(获取方式见下文)     
           
           > 如果你同时使用多个SendKey,请把它们都写在这个Secret的值中(用逗号间隔,不需要换行,开头和最后也不要加逗号)  
           > 
           > 像这样`key1,key2,key3,...`
         
         * 如推送TG Bot   
           `TG_CHAT_ID`填你或者你所在群的ID   
           `TG_CHAT_ID`填你Bot的Token(获取方式均见下文)    
         > **注意！填入内容注意前后不要有空格空行**   
         
         ![Secret](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Secret.png)
    
    * **微信Server酱**
    
    * [登陆Server酱](https://sct.ftqq.com/login)
      
      > PS:如果进入登陆界面后二维码无法显示，把二维码图片在新标签页打开即可
      > ![登陆界面](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Login.png)
    
    * 复制你的[SendKey](https://sct.ftqq.com/sendkey)备用
      ![SendKey](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/SendKey.png)
    
    * **TG Bot方面**
    
    * [获取ID](https://telegram.me/myidbot)    
    
    * [获取Token](https://telegram.me/BotFather)    

* **运行**
  
  * 点击上栏中间的Action进入运行日志页面，中间应该有个绿色按钮（I understand my workflow...），点击。
    ![image](https://user-images.githubusercontent.com/36188023/207884213-22fc13db-e420-40ab-a30d-d3ba404fa918.png)
  
  * 自动刷新后，会看到左边有一个叫`CVE-Monitor`的流程
  
  * 点进去，然后会看到有个黄条（this schedule was disabled......）
    ![image](https://user-images.githubusercontent.com/36188023/207884253-dfcff51f-3936-4cf4-9fe1-a385951ad417.png)
  
  * 点击 enable workflow 按钮
    
    > （并不是很确定是否都需要进行以上4个步骤，如果你没有出现这种情况，直接忽略掉好啦 = = ）  
  
  * 点击两次右上角的星星（star，在fork按钮的旁边）启动action
  
  * 再点击上面的Action选择`CVE-Monitor`流程 -> `build` -> `Monitor CVE` 就能看到每次的运行日志,看看有没有报错
  
  * 没有报错的话微信里应该就会有推送了
  
  * 最后，再检查一下Secrets页面，应该能看到`TOTAL_COUNT`那一栏显示刚刚更新了

## 补充

* 程序默认是每10分钟监测一下GitHub上有没有和CVE相关的repo更新，如果你想修改，可以在[AutoRun.yml](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/.github/workflows/AutoRun.yml)中依照[文档](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events)修改
  
  > **注意! 两次监测间隔时间不得小于5分钟**

* Tip: 在修改时，贴心的GitHub会提示间隔的时间  
  ![image](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/schedule.png)  

* 如果遇到什么问题或者有什么建议，欢迎在Issues中提出

参考:   
*https://github.com/kiang70/Github-Monitor/*  
*https://github.com/Hostage-02/AutoApi*
