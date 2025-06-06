### 配置Git步骤



#### 1. **安装 Git**

1. 下载后桌面/文件夹中右键git.bash表示打开git命令行
2. 打开cmd查看是否安装git:

```cmd
git --version
```

https://www.bilibili.com/video/BV1Hkr7YYEh8/?spm_id_from=333.1391.0.0&vd_source=35b804d0e534f391ec3606986f333f96

#### 2. **配置 Git**

1. 打开 Git Bash 或 CMD。

2. 配置用户名和邮箱：

   ```cmd
   $ git config --global user.name "你的用户名"
   $ git config --global user.email "你的邮箱"
   ```

3. 配置代理：

   ```cmd
   git config --global http.proxy http://127.0.0.1:端口号
   ```

   - 端口号可在 **控制面板 -> Internet 选项 -> 连接 -> 局域网设置** 中查看。

https://blog.csdn.net/weixin_43252521/article/details/123959391

#### 3. **生成 SSH 密钥**

1. 打开 Git Bash。

2. 运行以下命令生成 SSH 密钥：

   ```bash
   ssh-keygen -t rsa -b 4096 -C "你的邮箱"
   ```

   - 一直按 Enter 使用默认路径（`~/.ssh/id_rsa`）。

https://blog.csdn.net/weixin_42310154/article/details/118340458

#### 4. **添加 SSH 密钥到 SSH 代理**

1. 启动 SSH 代理：

   ```bash
   eval $(ssh-agent -s)
   ```

2. 添加 SSH 私钥：

   ```bash
   ssh-add ~/.ssh/id_rsa
   ```

#### 5. **添加 SSH 公钥到 GitHub**

1. 复制公钥内容：

   ```bash
   clip < ~/.ssh/id_rsa.pub
   ```

2. 登录 GitHub，进入 **Settings** > **SSH and GPG keys** > **New SSH key**。

3. 粘贴公钥，保存。

https://blog.csdn.net/qq_43775179/article/details/131805149

https://blog.csdn.net/YJ_VS_GY/article/details/127325813

#### 6. **测试 SSH 连接**

桌面右键代开git bash运行以下命令测试：

```bash
ssh -T git@github.com
```

- 看到 `Hi 用户名!` 表示成功。

  

#### 7. **在 IntelliJ IDEA 中配置 Git 和 SSH**

1. 打开 IDEA，进入 **File** > **Settings** > **Version Control** > **Git**。

   - 确保 Git 路径正确（如 `C:\Program Files\Git\bin\git.exe`）。

2. 进入 **Version Control** > **GitHub**，添加 GitHub 账号并勾选 **Clone git repositories using SSH**。

3. 进入 **Version Control** > **SSH**，添加私钥路径（如 `C:\Users\用户名\.ssh\id_rsa`）。

   

#### 8. **使用 SSH 推送代码**

1. 在 GitHub 上复制仓库的 SSH URL（如 `git@github.com:用户名/仓库名.git`）。
   - 一个项目对应一个库，上传新的项目需要创建一个库
2. 打开IDEA项目
   - 打开工具栏  **VCS** > **Create Git Repositor** > 选择路径创建git库在本文件
   - 打开工具栏 **Git**(如果为项目成功添加git会有此UI) > **Manager Remote** ->添加对应库的URL(注意：这里一定是仓库的SSH协议链接)
3. 提交代码：
   - 右键项目根目录，选择 **Git** > **Commit**，输入提交信息。
4. 推送代码：
   - 右键项目根目录，选择 **Git** > **Push**。
   - 如果 SSH 配置正确，IDEA 会直接推送，无需输入密码。



使用参考视频

https://www.bilibili.com/video/BV1V64y1z76k?spm_id_from=333.788.videopod.episodes&vd_source=35b804d0e534f391ec3606986f333f96&p=2



### 使用Git

#### 1.项目上传

在 Git 中，`add`、`commit` 和 `push` 是三个核心操作，它们分别用于将代码从工作区提交到本地仓库，再推送到远程仓库。以下是它们的作用和关系：

- **`add`**：标记更改，准备提交。
- **`commit`**：将更改保存到本地仓库。
- **`push`**：将本地更改同步到远程仓库。



**1. `git add`**

- **作用**：将工作区中的文件更改添加到暂存区（Staging Area）。
- **使用场景**：当你修改了文件后，需要将这些更改标记为准备提交的状态。

**2. `git commit`**

- **作用**：将暂存区中的更改提交到本地仓库，生成一个新的提交记录。
- **使用场景**：当你完成了一组相关的更改，并希望将这些更改保存为一个版本。

**3. `git push`**

- **作用**：将本地仓库中的提交推送到远程仓库（如 GitHub）。

- **使用场景**：当你希望将本地的更改同步到远程仓库时使用。

  

##### 三者的关系和流程

1. **工作区**：你修改文件的地方。
2. **暂存区**：通过 `git add` 将工作区的更改添加到暂存区。
3. **本地仓库**：通过 `git commit` 将暂存区的更改提交到本地仓库。
4. **远程仓库**：通过 `git push` 将本地仓库的更改推送到远程仓库。



#### 2.项目管理



- **提交代码**：**Commit** -> **Push**。

- **多次提交**：本地可多次提交，最终推送最佳版本。

- **分支开发**：创建分支 -> 修改代码 -> 推送分支。

- **查看历史**：通过 **History** 或 **Local Changes** 查看修改记录。



**1. 提交代码到远程仓库**

- 修改代码后，填写提交信息（注释），点击 **Commit**进入本地缓存。
- 点击 **Push**，将提交推送到远程仓库。



**2. 多次提交，推送最佳版本**

- 进入本地缓存后，可以继续修改并**Commit**。
- 最终选择最满意的版本，点击 **Push** 推送到远程仓库。



**3. 创建分支并开发**

- 在 IDEA 中点击右下角的 **Git Branches**，选择 **New Branch** 创建新分支。
- **checkout**切换到新分支后，修改代码并**Commit**。
- 点击 **Push**，将新分支推送到远程仓库，远程仓库中出现新分支。



**4. 查看修改历史**

- 右键点击文件，选择 **Git > Show History**，查看单个文件的修改记录。
- 在 **Local Changes** 窗口中，查看所有文件的更改状态。

























