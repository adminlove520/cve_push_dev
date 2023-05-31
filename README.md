# Github-CVE-Listener

![bulid](https://img.shields.io/badge/build-passing-brightgreen)
![actions](https://img.shields.io/badge/running%20on-Github%20Actions-orange)

```
 _______   ________  _________  ___   ___  __  __   _______                                                   
/______/\ /_______/\/________/\/__/\ /__/\/_/\/_/\/_______/\                                                  
\::::__\/_\__.::._\/\__.::.__\/\::\ \\  \ \:\ \:\ \::: _  \ \                                                 
 \:\ /____/\ \::\ \    \::\ \   \::\/_\ .\ \:\ \:\ \::(_)  \/_                                                
  \:\\_  _\/ _\::\ \__  \::\ \   \:: ___::\ \:\ \:\ \::  _  \ \                                               
   \:\_\ \ \/__\::\__/\  \::\ \   \: \ \\::\ \:\_\:\ \::(_)  \ \                                              
    \_____\/\________\/   \__\/    \__\/ \::\/\_____\/\_______\/                                              
 ______  __   __  ______       __        ________  ______  _________  ______  ___   __   ______  ______       
/_____/\/_/\ /_/\/_____/\     /_/\      /_______/\/_____/\/________/\/_____/\/__/\ /__/\/_____/\/_____/\      
\:::__\/\:\ \\ \ \::::_\/_    \:\ \     \__.::._\/\::::_\/\__.::.__\/\::::_\/\::\_\\  \ \::::_\/\:::_ \ \     
 \:\ \  _\:\ \\ \ \:\/___/\    \:\ \       \::\ \  \:\/___/\ \::\ \   \:\/___/\:. `-\  \ \:\/___/\:(_) ) )_   
  \:\ \/_/\:\_/.:\ \::___\/_    \:\ \____  _\::\ \__\_::._\:\ \::\ \   \::___\/\:. _    \ \::___\/\: __ `\ \  
   \:\_\ \ \ ..::/ /\:\____/\    \:\/___/\/__\::\__/\ /____\:\ \::\ \   \:\____/\. \`-\  \ \:\____/\ \ `\ \ \ 
    \_____\/\___/_(  \_____\/     \_____\/\________\/ \_____\/  \__\/    \_____\/\__\/ \__\/\_____\/\_\/ \_\/ 
```

Get latest CVE EXP/POC from GitHub in WeChat!

## Tips

* The Program runs with Github Actions, no need to use your own server

* [Chinese Version](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/README_ZH.md)
  
  ## Usage

* **preparations**
  
  * **GitHub**
    
    * fork my repo   
      Sign up or log into your GitHub account and click the "fork" button on the page  
      ![Fork](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Fork.png)  
      After that, a repo with the same name will show up in your account.   
      Follow the steps below in **your repository**
    
    * Create a new GitHub Personal Access Token    
        1）Go to the New Token [Page](https://github.com/settings/tokens/new)  
        2）Set note to `GH_TOKEN` , select "repo"，set expiration to no expiration，click `Generate token` ，and remember to **COPY AND SAVE** your token  
      
      > **Attention! Once you leave the page, you won't able to see your token any more!**  
      
        ![Fork](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Token.png)
    
    * Create a new repository secret   
      
      1. Go to Setting -> Secrets -> New repository secret，Create 6 secrets：`GH_TOKEN` `SCKEY`  `TOTAL_COUNT` `OPTION` `TG_CHAT_ID` `TG_TOKEN`
         
         > **Don't create the secrets you don't need**
      
      2. Update the values  
         
         The value of `OPTION`: `1` for pushing to WeChat, `2` for using Telegram bot,  `3` for using all of them    
         The value of  `GH_TOKEN`: Your GitHub Personal Access Token  
         The value of  `TOTAL_COUNT`: 0     
         
         * If you want to sent message to WeChat      
           The value of  `SCKEY`: Your SendKey   
           
           > If you are using multiple SendKeys, please include them all in the value of the secret,separated by commas and without any line breaks or leading/trailing commas.
           > 
           > For example:
           > 
           > ```
           > key1,key2,key3,...
           > ```
         
         * If you want to sent message to Telegram     
           The value of `TG_CHAT_ID`: Your ID or the group's ID    
           The value of `TG_TOKEN`: The bot's token
      
      > **No spaces or line breaks is allowed at either the start or the end**  
      
        ![Secret](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Secret.png)
      
      * **WeChat ”Server-Chan“**
    
    * [Log in](https://sct.ftqq.com/login)
      
      > Notice: If the QR Code doesn't load, try to open the image in a new tab
      > ![image](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/Login.png)
    
    * Copy your [SendKey](https://sct.ftqq.com/sendkey) for later use
      ![SendKey](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/SendKey.png)
      
      * **Telegram Bot**   
    
    * [Get Your ID](https://telegram.me/myidbot)    
    
    * [Get Your Token](https://telegram.me/BotFather)    

* **Run the program**
  
  * Go to the Action Tab，Click the green button（I understand my workflow...) in the middle
    ![image](https://user-images.githubusercontent.com/36188023/207883085-f9345925-734a-48db-a7c6-693b0eabd7b8.png)
  
  * After refreshing the page，you'll see a workflow called `CVE-Monitor`.
  
  * Select the `CVE-Monitor` workflow，You'll see a notice（this schedule was disabled......）
    ![image](https://user-images.githubusercontent.com/36188023/207883473-e1b6a053-54b5-4c4e-85f7-fef549672cd0.png)
  
  * Press `enable workflow` button
    
    > （If you didn't experience the problem, just ignore what I've just said = = ）  
  
  * Click star twice to start the workflow
  
  * Go to Action tab -> `CVE-Monitor` workflow -> `build` -> `Monitor CVE` You'll see the logs of each workflow run, just check if there're any errors
  
  * Normally, you'll receive a message now
  
  * Last，if the program functioned correctly, secret `TOTAL_COUNT` should be updated 

## Other info

* The workflow is currently configured to run every 10 minutes，if you want to change that，go to [AutoRun.yml](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/.github/workflows/AutoRun.yml), be sure to read the [GitHub Docs](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events).
  
  > **Attention! Actions schedules run at most every 5 minutes.**

* Tip: GitHub will tell you the meaning of the schedule expression while you are changing it
  ![image](https://github.com/Kira-Pgr/Github-CVE-Listener/blob/main/Images/schedule.png)  

ref:   
*https://github.com/kiang70/Github-Monitor/*  
*https://github.com/Hostage-02/AutoApi*

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Kira-Pgr/Github-CVE-Listener&type=Date)](https://star-history.com/#Kira-Pgr/Github-CVE-Listener&Date)
