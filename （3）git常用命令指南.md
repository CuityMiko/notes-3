#git-常用命令指南

 git简易使用指南，没有太多复杂内容^_^！       

****   
##创建新仓库
**git init**  *初始化本地git仓库（创建新仓库）*       

**** 

##配置
**git config --global user.name "xxx"**                   *配置用户名*         
**git config --global user.email "xxx@xxx.com"**          *配置邮件*  

**** 

##检出仓库
**git clone /path/to/repository**                         *clone本地仓库（检出仓库）*        
**git clone username@host:/path/to/repository**           *clone远程仓库（检出仓库）*   

**** 

##添加与提交
**git add xyz**                                       *添加xyz文件至缓存区*               
**git add .**                                             *添加当前子目录下所有更改过的文件至缓存区*              
**git commit -m "代码提交注释信息"**                                      *提交*               
**git commit --amend -m  "代码提交注释信息"**                              *合并上一次提交（用于反复修改）*                  
**git commit -am "代码提交注释信息"**                                      *将add和commit合为一步*                        
>现在，你的改动已经提交到了 HEAD，但是还没到你的远端仓库

**** 

##推送改动
**git push origin master**                                    *将当前分支push到远程master分支，可以把 master 换成你想要推送的任何分支*               
**git push origin :feature/ABCD123**                       *删除远程仓库的feature/ABCD123分支*             
**git push --tags**                                           *把所有tag推送到远程仓库*                     
**git remote add origin <server\>**    *如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，使用该命令就可以将你的改动推送到所添加的服务器上去了（用于push/pull/fetch）*           
**git revert dfb02e6e4f2f7b573337763e5c0013802e392818**       *撤销提交dfb02e6e4f2f7b573337763e5c0013802e392818*

**** 

##分支   
**git checkout -b feature_x**    *从当前分支创建新分支feature_x并检出*                    
**git checkout master**    *切换回主分支*                 
**git branch -d feature_x**     *把新建的feature_x分支删掉*                
**git branch**                                                *显示本地分支*          
**git branch --contains 50089**                               *显示包含提交50089的分支*               
**git branch -a**                                            *显示所有分支*               
**git branch -r**                                             *显示所有原创分支*             
 >除非你将分支推送到远端仓库，不然该分支就是*不为他人所见的*
**** 

##更新与合并
**git fetch**                                                 *获取所有远程分支（不更新本地分支，另需merge）*                  
**git fetch --prune**                                         *获取所有原创分支并清除服务器上已删掉的分支*                     
**git pull origin master**                                    *获取远程分支master并merge到当前分支*            
**git diff**                                                  *显示所有未添加至index的变更*                  
**git diff --cached**                                         *显示所有已添加index但还未commit的变更*           
**git diff HEAD^**                                            *比较与上一个版本的差异*
**git diff HEAD -- ./lib**                                    *比较与HEAD版本lib目录的差异*                    
**git diff origin/master..master**                      *比较远程分支master上有本地分支master上没有的*                     
**git diff origin/master..master --stat**            *只显示差异的文件，不显示具体内容*                 


**** 

##标签
**git tag**                                    *显示已存在的tag*         
**git tag 1.0.0 1b2e1d63ff**       *创建一个叫做 1.0.0 的标签，1b2e1d63ff 是你想要标记的提交 ID 的前 10 位字符*            
>使用如下命令获取提交 ID：*git log*
**** 

##日志
**git log**                                                     *显示提交日志*                
**git log --stat**                                          *显示提交日志及相关变动文件*                
**** 

##其他
**git status**                                                *查看当前版本状态（是否修改）*            
**git rm xxx**                                               *删除文件xxx*                     
**git rm -r**                                                 *递归删除*      
**git show dfb02e6e4f2f7b573337763e5c0013802e392818**         *显示某个提交的详细内容*                  
**git show HEAD**                                             *显示HEAD提交日志*                     
**git show HEAD^**                                            *显示HEAD的父（上一个版本）的提交日志 ^^为上两个版本 ^5为上5个版本*     
**git show v2.0**                                                 *显示v2.0的日志及详细内容*            
**git show-branch**                                           *图示当前分支历史*                 
**git show-branch --all**                                     *图示所有分支历史*                     
