vim setting:

安装vim之后：
把vimrc配置文件放到用户目录/etc/vim/目录下
把.vim目录放到用户根目录下~/

然后进入vim，使用:PluginInstall就可以安装插件(其实不用这部，因为插件都在上面打包好了)。


=== vim-elixir ===

安装vim-elixir可以使vim支持elixir，在这之前要先安装syntastic，执行下面命令：
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
如果没有安装curl先安装：sudo apt-get install curl
然后在vimrc配置文件中加上下面命令即可:
execute pathogen#infect()


=== 安装ctrlp插件 ===

Bundle 'ctrlpvim/ctrlp.vim'
" 常规模式下输入：:CtrlP 或者 按键盘Ctrl + p 调用插件，可以查找项目文件
安装代码搜索插件Ag/Ack:
先安装Ag:apt-get install silversearcher-ag


=== 安装Ack ===

Plugin 'mileszs/ack.vim'
let g:ackprg = 'ag --nogroup --nocolor --column'
运行vim可以用 :Ack xxx 搜索项目代码


=== 安装YouCompleteMe ===

(安装过程下载太慢，备好梯子！！！)
在.vimrc中添加下列代码
Bundle 'Valloric/YouCompleteMe'
保存退出后打开vim，在正常模式下输入
:BundleInstall
等待vundle将YouCompleteMe安装完成
然后打开终端：（确保用的源和已经安装的包是最新的 sudo apt-get update 和 sudo apt-get -f upgrade）
sudo apt-get install build-essential cmake
sudo apt-get install python-dev python3-dev
cd ~/.vim/bundle/YouCompleteMe
./install.py --clang-completer
做这步操作的时候提示：
File /home/holtom/.vim/bundle/YouCompleteMe/third_party/ycmd/build.py does not exist; you probably forgot to run:
    git submodule update --init --recursive

执行：git submodule update --init --recursive（有点久。。。好久。。。）

之后再一次 ./install.py --clang-completer 

如果提示： ERROR: please install CMake and retry.
则安装CMake:下载CMake包：
1、tar -xzvf cmake-2.8.9.tar.gz
2、cd cmake-cmake-2.8.9
3、./bootstrap
4、make
5、sudo make install

之后再一次 ./install.py --clang-completer
下载clang的时候太慢，老是失败，手动下载clang包放到指定目录：
/home/holtom/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/../clang_archives/clang+llvm-4.0.0-x86_64-linux-gnu-ubuntu-14.04.tar.xz

最后再一次 ./install.py --clang-completer

等待完成！！！
