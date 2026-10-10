# 大部分图片来自网络，一部分来自艺术学校内老师示范作品和学生作品

***如果我在这里上传的图片侵犯了您的权益（版权问题），您可以在评论区提醒我，我会将相关图片从仓库移除***

我从我的老师们得到了这些速写素材，有很小的一部分是 AI 生成的图片，但是我并没有找到 AI 水印标记。

> 说真的，我感觉 AI 生成的速写实在是不尽人意，就像在开盲盒一样，有的时候并不适用于考试，可能甚至连最基本的美观都做不到。

我决定把这些好看的速写画作分享到这里（其实是我想找别的地方存放），并不定期添加内容。


## 快速跳转通道

[速写素材_头部素材](https://github.com/ln1325/Sketching-materials-for-the-art-college-entrance-examination/tree/main/%E9%80%9F%E5%86%99%E7%B4%A0%E6%9D%90_%E5%A4%B4%E9%83%A8%E7%B4%A0%E6%9D%90)

---

## 遇到“图片打不开 / 无法下载”时的排查与解决（常见步骤）

下面的说明可以直接粘到 Issue 回复里，或者在本仓库 README 中查阅。

1) 先尝试打开图片的 Raw 链接（直接下载原始文件）

   - 例如本仓库中某张图片的 Raw URL 格式为：

     https://raw.githubusercontent.com/ln1325/Sketching-materials-for-the-art-college-entrance-examination/main/%E9%80%9F%E5%86%99%E7%B4%A0%E6%9D%90_%E5%A4%B4%E9%83%A8%E7%B4%A0%E6%9D%90/IMG_0137.JPG

   - 将上面的链接复制到浏览器新标签打开，或右键图片选择“在新标签页中打开图像”。如果能显示或下载，则说明文件本身没问题。

2) 命令行下载（便于排查返回的错误信息）

   - 查看响应头（把输出贴过来便于诊断）:

     curl -I "<raw-url>"

   - 下载文件（Linux / macOS）:

     curl -L -o IMG_0137.JPG "<raw-url>"

     或者：

     wget -O IMG_0137.JPG "<raw-url>"

   - Windows PowerShell:

     Invoke-WebRequest -Uri "<raw-url>" -OutFile .\IMG_0137.JPG

3) 用 git 克隆仓库（若用户不熟命令行，推荐直接克隆后本地打开）

   git clone https://github.com/ln1325/Sketching-materials-for-the-art-college-entrance-examination.git

   然后在本地打开对应路径下的图片：`速写素材_头部素材/IMG_0137.JPG`。

4) 如果克隆后打开文件得到的是文本（而不是图片），请检查是否为 Git LFS 指针文件

   - 用文本查看前几行（不要用图片查看器）：

     head -n 5 速写素材_头部素材/IMG_0137.JPG

     如果内容类似：

     version https://git-lfs.github.com/spec/v1
     oid sha256:...
     size ...

     那就不是图片二进制文件，而是 Git LFS 的指针。

   - 解决方法：

     1. 安装 Git LFS（如果还没装）：

        git lfs install

     2. 拉取 LFS 文件并替换指针：

        git lfs pull

     3. 或者在已有仓库里：

        git lfs fetch --all
        git lfs checkout

5) 提前预防与仓库设置建议

   - 如果仓库中包含大批量或较大的二进制图片，考虑在 README 中写明如何安装 Git LFS 并拉取大文件；也可以在 Releases 发布打包的 ZIP，或提供外部下载链接，方便不熟命令行的用户。

   - 如果可能，避免文件名中包含空格或非常规字符（虽然 GitHub 通常能处理中文路径，但有些工具或脚本对编码敏感）。

   - 若使��� Git LFS，请在仓库根目录添加 .gitattributes（示例）：

     ```.gitattributes
     *.jpg filter=lfs diff=lfs merge=lfs -text
     *.jpeg filter=lfs diff=lfs merge=lfs -text
     *.png filter=lfs diff=lfs merge=lfs -text
     ```

6) 给遇到问题的访客的快速回复模板（可直接复制到 Issue 或回复里）

   模板 A（先试 Raw / 下载）:

   > 你好！谢谢反馈。请先尝试打开文件的 Raw 链接（右上 “Raw” 或直接使用 raw.githubusercontent.com 的 URL），或者用命令行下载试试（curl/wget/PowerShell）。如果仍然打不开，请把浏览器的报错（如 403/404）或你下载后文件的前几行（用记事本打开）发给我，我来帮你看。

   模板 B（可能是 Git LFS）:

   > 如果你克隆仓库后打开图片看到的是文本（开头类似 "version https://git-lfs.github.com/spec/v1"），说明这是一个 Git LFS 指针文件；请运行：
   >
   > ```
   > git lfs install
   > git lfs pull
   > ```
   >
   > 运行后再打开图片应该就正常了。


---

如果你希望我把 README 的这一改动再做得更短或更长，或者把说明移到某个子目录下的 README，我可以继续修改（现在我已把这份说明合并到主 README 中）。