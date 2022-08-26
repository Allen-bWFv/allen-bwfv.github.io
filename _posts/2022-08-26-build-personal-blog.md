## 创建gitpage仓库

在github上创建一个新的仓库，Repository name 填your_user_name.github.io, 例如我的仓库名是 allen-bwfv.github.io。
如果用户名如果有大写，这里直接全小写就可以了。

## 找一个自己喜欢的主题
[jekyllthemes](http://jekyllthemes.org/)这里找一个自己喜欢的主题，然后会有多种使用方式，我这里直接把主题仓库下载到本地，如果是克隆记得删除 **.git** 。

## 安装Jekyll本地编译环境
我这里是windows环境
安装ruby，[下载地址](https://rubyinstaller.org/downloads/)，一路正常安装，有个选择安装MSYS2和development toolchain记得选两个都装
然后依次执行，安装过程比较慢，可以忙会别的
 ```sh
gem install bundle
 
gem install jekyll

gem install github-pages 
 ```
然后到自己的目录下（刚下载的主题目录）
执行
 ```sh
bundle install
```
这里如果有报错，可以根据具体报错去解决，我这里预到超时问题，执行以下命令后解决
```sh
gem update --system
gem update bundler
```
然后尝试启动预览
```sh
bundle exec jekyll serve -P 5555 --watch
```
我这里又遇到缺少依赖的问题，根据提示加上就可以了，我这里缺少wdm和webrick
所以在Gemfile文件中添加
```cmd
gem 'wdm', '~> 0.1.1', :install_if => Gem.win_platform?
gem "webrick", "~> 1.7"
```
然后再次执行bundle install
再启动预览就正常了
再浏览器输入
http://localhost:5555
就可以预览博客了

然后把文件推到仓库，在浏览器里输入 https://allen-bwfv.github.io/ 这个地址l就可以访问了。
