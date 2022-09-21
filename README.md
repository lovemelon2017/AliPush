# AliPush

阿里推送测试


#TODO Android普通应用改造系统应用

方式一：JDK1.8
1.清单文件加 android:sharedUserId="android.uid.system"

2.studio打包出apk

3.获取到系统签名文件 platform.pk8 platform.x509.pem

4.使用signapk.jar 命令打出系统签名包  ( 自行下载 signapk.jar )

   java -jar signapk.jar platform.x509.pem platform.pk8 app-release.apk systemApp.apk

方式二：
1.清单文件加 android:sharedUserId="android.uid.system"

2.使用keytool-importkeypair工具生成签名文件keystore

3.studio使用keystore打包应用

    keytool-importkeypair下载地址：https://github.com/getfatday/keytool-importkeypair
    
 说明：keytool-importkeypair 使用的是shell脚本，Windows不能直接使用，可以将后缀名改成 xxx.sh
           使用git执行脚本文件
      
    keytool-importkeypair.sh -k ~/hanchao.keystore -p 123456 -pk8 platform.pk8 -cert platform.x509.pem -alias     platform

1. -k 表示要生成的 keystore 文件的名字，这里命名为 release.keystore
2. -p 表示要生成的 keystore 的密码，这里是 youPassword
3. -pk8 表示要导入的 platform.pk8 文件
4. -cert 表示要导入的platform.x509.pem
5. -alias 表示给生成的 release.keystore 取一个别名，这是命名为 youAlias





2、（先进入项目文件夹）通过命令 git init 把这个目录变成git可以管理的仓库

git init

3、把文件添加到版本库中，使用命令 git add .添加到暂存区里面去，不要忘记后面的小数点“.”，意为添加文件夹下的所有文件

git add .

4、用命令 git commit告诉Git，把文件提交到仓库。引号内为提交说明

git commit -m 'first commit'

5、关联到远程库

git remote add origin 你的远程库地址
如：

git remote add origin https://github.com/githubusername/demo.git

6、获取远程库与本地同步合并（如果远程库不为空必须做这一步，否则后面的提交会失败）

git pull --rebase origin master

7、把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。

git push -u origin master
————————————————

