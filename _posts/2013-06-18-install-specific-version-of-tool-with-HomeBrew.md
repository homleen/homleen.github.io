---
layout: post
title: 通过Homebrew安装指定/旧版本的软件
category: tools
---

Homebrew是Mac平台下的一款包管理工具，同apt-get、yum等工具一样，它可以让你更轻松的在OS X上安装和卸载一些开源软件。

通常情况下，`brew install` 会选择安装最新版本package。如果想要安装指定版本的package，可以参考以下步骤。

{% highlight bash %}

# update
brew update

# 如果brew update遇到问题，也可以通过以下命令进行更新
cd $(brew --prefix) && git pull --rebase

# 以postgresql为例
brew versions postgresql

# Output:
# 9.1.3    git checkout e088818 /usr/local/Library/Formula/postgresql.rb
# 9.1.2    git checkout dfcc838 /usr/local/Library/Formula/postgresql.rb
# 9.1.1    git checkout 4ef8fb0 /usr/local/Library/Formula/postgresql.rb
# 9.0.4    git checkout 2accac4 /usr/local/Library/Formula/postgresql.rb
# 9.0.3    git checkout b782d9d /usr/local/Library/Formula/postgresql.rb
# 9.0.2    git checkout 2c3b88a /usr/local/Library/Formula/postgresql.rb
# 9.0.1    git checkout b7fab6c /usr/local/Library/Formula/postgresql.rb
# 9.0.0    git checkout 1168d8f /usr/local/Library/Formula/postgresql.rb
# 8.4.4    git checkout c32bea0 /usr/local/Library/Formula/postgresql.rb
# 8.4.3    git checkout 9b2ef7c /usr/local/Library/Formula/postgresql.rb
# 8.4.1    git checkout 0495cf5 /usr/local/Library/Formula/postgresql.rb
# 8.4.0    git checkout a82e823 /usr/local/Library/Formula/postgresql.rb

git checkout a82e823 /usr/local/Library/Formula/postgresql.rb
brew install postgresql

{% endhighlight %}

如果你已经安装某个版本的package，可以先通过`brew unlink postgresql` 解除链接。

### P.S

* Homebrew通过git来管理自己，默认情况下，其git目录存放在 `/usr/local`，你也可以通过`cd $(brew --prefix)` 进入该目录。

* 可以通过`brew link` 和 `brew unlink` 进行某个package的版本切换。
