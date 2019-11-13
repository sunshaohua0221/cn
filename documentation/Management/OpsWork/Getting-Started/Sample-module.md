# 构建模板

1. 在模板管理页面点击**创建**，跳转至编辑模板页面

![](../../../../image/opswork/Sample-1.PNG)

2. 在编辑模板页面填写名称和描述

   注意：**名称不可以重复**，且必填

3. 按下方的**加号图标**添加操作,出现弹窗。

4. 选择**安装tomcat**，点击**确定**

![](../../../../image/opswork/Sample-2.PNG)

5. 此时模板中出现了**安装tomcat**的YAML 描述。如图所示：

![](../../../../image/opswork/Sample-3.PNG)

6. 继续添加操作，这次选择**命令-执行shell命令**，用来编辑启动tomcat命令：
  ```shell
  将 echo hello
  替换为：
  sh /usr/opt/tomcat-8.5.38/bin/startup.sh
  ```

7. 点击**保存并执行**
