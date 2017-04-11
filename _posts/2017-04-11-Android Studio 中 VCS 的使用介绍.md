---
layout: post
title: "Android Studio 中 VCS 的使用介绍"
date: 2017-04-11 
description: "翻译自 Saúl Molinero 的 The VCS client of Android Studio"
tag: 博客 Android 翻译
---   

翻译自 Saúl Molinero 的 [The VCS client of Android Studio](http://saulmm.github.io/vcs-android-studio)

现在，我们无法想象在没有版本控制系统的情况下开始一个新的软件项目，在不同的选项可用于VCS，Git，毫无疑问，已经成为其中最流行的系统之一，像Subversion或Mercurial。

然而，这种工具需要的**学习曲线通常非常陡**，因为版本控制系统包括的各种特征和选项使得它同时变得复杂和强大。

对于大多数实验开发者和初学者来说，使用好的工具或足够好的定制环境以便以有效和快速的方式处理VCS是重要的。

### 对比

在我们可以使用版本控制系统的好处可以发现一个强大的功能是**随时间比较文件与其各自的状态**。为此，JetBrains包括最强大和直观的 **diff / merge**工具之一

良好的使用这些工具可以加快日常工作，因为这些比较是频繁的，当我们修改代码（添加，删除或更改行），除了查看它。 此外，这些修改往往很难表示，所以不是很容易找到一个很好的工具来显示这些变化清楚。

### IntelliJ as a diff, merge tool

从IntelliJ IDEA的2016版本开始，JetBrains包含了一个有趣的功能，称为 **Create command line launcher**，Android Studio在其2.2更新中继承。
![输入图片说明](https://static.oschina.net/uploads/img/201703/20152221_vPbg.png "在这里输入图片标题")

这个新功能允许在外部使用IntelliJ或Android Studio中使用的**diff / merge**工具。以这样的方式，我们可以从命令行或从我们最喜欢的第三方VCS客户端使用它。
![输入图片说明](https://static.oschina.net/uploads/img/201703/20152420_fqmg.gif "在这里输入图片标题")

因此，在其他有趣的情况下，我们可以解决冲突或使用这些外部工具比较不同的文件，这是真的很方便。作为替代，像Kaleidoscope或Filemerge的工具也面向这个目的。

我通常使用的VCS外部客户端是SourceTree，由Atlassian提供。 要将Android Studio diff / merge工具设置为SourceTree的默认工具，我们只需要在SourceTree Settings / Diff的设置部分设置IDE创建的二进制文件（默认为/ user / local / bin / ,将外部工具设置为其他正确的参数。![输入图片说明](https://static.oschina.net/uploads/img/201703/20164021_827Z.png "在这里输入图片标题")

### 将当前文件与分支进行比较

IntelliJ IDEA和Android Studio允许将对比编辑器中打开当前的文件和在不同分支中的相应版本进行比较。 这在各种情况下可能很有意思，例如查看代码，验证冲突是否已正确解决等。

此功能称为 分支比较，在VCS菜单中或使用查找操作（⌘+ A）输入功能名称的一部分时可用。

选择VCS（本地和远程版本）中存在的任何分支后，将立即显示差异工具，以便比较分支之间的更改。 
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/compare_with_branch.gif "在这里输入图片标题")
### 与以前的提交进行比较

Compare with ...的特点将允许我们使用对话框去选择先前提交的内容，以便将从该点所做的更改与文件的当前状态进行比较。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/compare_with-history.gif "在这里输入图片标题")
如果我们想显示当前文件已经改变的历史提交记录,我们可以使用Show history ...功能，它将使用IDE底部显示的固定面板来实现此目的。

### 处理改变
通常，修改一些文件后，可能有助于检查从最后一次提交（尚未提交的更改）做了哪些更改。本地更改将把焦点放在底部面板中，显示所有尚未提交的本地修改。在本地更改面板上，我们可以执行一些功能，而不需要将手从键盘：

使用 diff工具显示差异从最后一次提交的更改
Show the diff tool with the changes made from the latest commit - ( ⌘ + D )
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/local_changes_diff.gif "在这里输入图片标题")

### Revert changes - ⌥ + ⌘ + Z

此外，此功能可以在日志之外的更多上下文中使用，对任何文件使用恢复⌥+⌘+ Z，将显示还原对话框，允许还原最近提交的修改。

![输入图片说明](http://saulmm.github.io/resources/cvs-studio/local_changes_revert.gif "在这里输入图片标题")
注意：通常，IntelliJ / Android Studio中显示的对话框可以使用快捷方式标签+ enter关闭。

### VCS的日志

尽管，个人而言，我更喜欢第三方VCS客户端像SourceTree（它有一个很好的方式显示日志），Android Studio和IntelliJ也实现了这个功能，通过查找功能找到操作显示VCS日志或在VCS菜单下找到它。

![输入图片说明](http://saulmm.github.io/resources/cvs-studio/vcs_log.gif "在这里输入图片标题")

作为优点，集成在IDE中，它利用IntelliJ的所有导航技能。 因此，我们可以用一个非常容易和快速的方式用不同的按键与日志交互。

如果我们选择某个提交，我们可以通过查找action_（⇧+⌘+ A）到与所选提交相关的有意思的功能，如复位，检出，使用（⌘+ D）等。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/vcs_log_diff.gif "在这里输入图片标题")

### VCS 操作窗口 ( ⌥ + V )
我们可以显示一个对话框来使用VCS最常用的操作，如：commit，branches，stash等。使用快捷方式（⌥+ V）。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/vcs_dialog.gif "在这里输入图片标题")

### 快速提交 - （⌘+ K）+（Tab + Enter）
使用快捷键（⌘+ K）+（⇥+ Enter）打开集成在Android Studio或IntelliJ中的VCS客户端，我们可以在少于5秒内准备好提交。 此外，还有一些有趣的功能，我们可以在提交之前启用，如代码检查，organize 和 etc.导入等。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/quick_commit.gif "在这里输入图片标题")

### GitHub集成
IntelliJ，Android Studio和其他JetBrains环境中，我们可以利用与GitHub的集成，在设置我们的凭据后，我们将能够使用一些有用的功能与社交编码平台交互。

### 获取到存储库的直接Web链接
从文件浏览器或编辑文件，在GitHub上打开的功能将打开一个带有该文件的远程版本的浏览器。 此外，如果我们运行这个功能.选择的文本，相同的文本将在GitHub版本创建的链接高亮显示
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/github_open.gif "在这里输入图片标题")

### 创建请求(PR)
有一种方法可以直接从编辑器创建拉取请求，使用功能Create Pull Request（通常通过find操作访问），IDE将提示一个对话框，询问base branch和candidate for merge。 填写表单后，将在GitHub上创建一个pull请求。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/github_pr.gif "在这里输入图片标题")

### 创建Gist
同样，我们可以在Android Studio中的GitHub上创建私有，匿名和公开的Gists，并使用Create Gist的功能。
![输入图片说明](http://saulmm.github.io/resources/cvs-studio/github_gist.gif "在这里输入图片标题")