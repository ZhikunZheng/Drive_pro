

![image-20230907231131121](C:\Users\ZZK\AppData\Roaming\Typora\typora-user-images\image-20230907231131121.png)

0.git init 初始化当前目录为一个git仓库

1.git add filename		(工作区  --->   暂存区)      git add .  添加所有工作区文件到暂存区

2.git commit  -m "备注信息"	(暂存区  --->   本地仓库)

3.git log 查看提交信息

4.git status 工作区和暂存区有哪些文件

5.git reset --hard commitlD 版本回退 （选中视为复制，点击滚轮在当前指针位置处粘贴）

6.撤销掉回退

​	法1：利用被回退掉提交的提交id，但clear掉页面后就找不到了

​	法2：git reflog 获取过去操作信息，通过分析获得需要的commitID

7.设置.gitignore文件，eg.*.a  --- 不管理所有.a文件

8.git branch查看分支

9.git branch name 创建分支

10.git checkout name 切换分支

11.git checkout -b name 创建并且切换到新分支

12.git merge dev01 合并分支

​		退出merge编辑：ESC + ：+ wq

13.git branch -d dev02 删除分支（不能删除当前分支，只能删除其他分支）

### 解决冲突

冲突：比如两个分支对file01文件同一行进行修改，进行合并分支时会产生冲突，报错如下

![253a75cc414dd9b87a6c3148e964770](C:\Users\zzk\AppData\Local\Temp\WeChat Files\253a75cc414dd9b87a6c3148e964770.png)

git的处理方式如下：将文件写成如下形式,用户进行手动解决冲突

![a397ad8d163f15ab6671157e7610f64](C:\Users\zzk\AppData\Local\Temp\WeChat Files\a397ad8d163f15ab6671157e7610f64.png)

![image-20230909161254019](C:\Users\zzk\AppData\Roaming\Typora\typora-user-images\image-20230909161254019.png)



分支使用原则与流程

![image-20230909161842288](C:\Users\zzk\AppData\Roaming\Typora\typora-user-images\image-20230909161842288.png)

git batch -D name （强制删除）使用情况：当name中的修改没有merge到当前分支中时，-d无法删除，此时使用-D能强制删除

### .bashrc	命令行命令别名

#用于输出git提交日志
alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'
#用于输出当前目录所有文件及基本信息
alias ll='ls -a'





## 使用码云(gitee)模拟公司实际使用

公司中常用GitLab，因为部署在本地，而github和gitee都是部署在别人的服务器上

设置正确的用户邮箱（gitee认证，访问私密仓库）：

```bash
git config --global user.name "zzk921"
git config --global user.email "2920204447@qq.com"
```

配置SSH公钥

```bash
ssh-keygen -t rsa
```

### Gitee设置账户公钥

获取公钥

```bash
cat ~/.ssh/id_rsa.pub
```

![image-20230909171649298](C:\Users\zzk\AppData\Roaming\Typora\typora-user-images\image-20230909171649298.png)

验证是否配置成功

```bash
ssh -T git@gitee.com
```

