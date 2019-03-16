## 允许下载应用任何来源

`sudo spctl --master-disable`

## HomeBrew安装

- [镜像安装]( https://www.jianshu.com/p/97b2552fed42)

  - 获取brew_install

  `curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install >> brew_install`

  - 编辑brew_install

    `BREW_REPO = "git://mirrors.ustc.edu.cn/brew.git".freeze
    CORE_TAP_REPO = "git://mirrors.ustc.edu.cn/homebrew-core.git".freeze`

  - 安装brew

    `/usr/bin/ruby ./brew_install`

  - 替换源

    ```
    cd "$(brew --repo)"
    git remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git
    
    cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
    git remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
    
    brew update
    ```

  - 替换bintray镜像

    `echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.bash_profile
    source ~/.bash_profile`

- [官网安装](https://brew.sh/index_zh-cn)

  `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

- 禁止brew自动更新

  `vim ~/.base_profile `

  `export HOMEBREW_NO_AUTO_UPDATE=true`

- `brew doctor`

## home-cask

- `brew tap caskroom/cask`

## 常用指令

```
brew search xxx
brew install xxx
brew config
brew cask install xxx

brew uninstall xxx
brew cask uninstall xxx

brew outdated 查看哪些已安装的程序需要更新
brew upgrade 更新所有包
brew upgrade xxx 更新指定包
brew cleanup -n 列出需要清理的内容
brew cleanup xxx 清除老版本

brew list

brew install git 
```

## iterm2

```
brew install zsh zsh-completions
brew cask install iterm2
```

- 设置
  - 打开默认为iterm2   `iterm2 ->make iterm2 deafult term`

  - 热键 `iterm2 -> perferences -> keys -> hotkey`

  - bash切换zsh 

    ```
    查看zsh路径: which zsh
    shell切zsh: chsh -s /usr/local/bin/zsh
    切回bash:   chsh -s /bin/bash
    重新打开可以看到效果
    查看当前shell:  echo $SHELL
    zsh生效bash配置: vi .zshrc  添加source ~/.bash_profile
    ```

    

## oh-my-zsh

- 安装参照 https://github.com/robbyrussell/oh-my-zsh

- 主题设置     https://blog.csdn.net/gangyin5071/article/details/79601132

  - 安装命令

    `sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"`

  - 挑选选择合适[主题](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes) 

    ```
    vi .zshrc
    ZSH_THEME="agnoster" --修改
    ```

  - agnoster要下载安装[Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)字体，否则会有乱码

  - 应用字体到iterm2，`iTerm -> Preferences -> Profiles -> Text -> Change Font`

  - 重新打开生效

  - 插件

    [自带的插件](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins) 

    其他的要先安装  eg `brew install zsh-autosuggestions zsh-syntax-highlighting`

    ```
    vi .zshrc
    修改 plugins=(autojump zsh-autosuggestions git zsh-syntax-highlighting)
    添加
    source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
    source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
    ```


## NVM   NPM

- 安装

  `wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash`

- 改镜像

  ```
  export NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node
  export NVM_IOJS_ORG_MIRROR=https://npm.taobao.org/mirrors/iojs
  ```

- 常用指令

  ```
  nvm install <version>
  nvm uninstall <version>
  nvm ls
  nvm ls-remote
  nvm current
  nvm use <version>
  nvm alias <name> <version> 添加别名
  nvm alias default <version> 默认版本
  nvm unalias <name>
  ```

- NPM配置

  ```
  还原
  npm config set registry  https://registry.npmjs.org
  淘宝镜像
  npm config set registry https://registry.npm.taobao.org --global
  npm config set disturl https://npm.taobao.org/dist --global
  cnpm
  npm --registry=https://registry.npm.taobao.org install cnpm -g   --cnpm
  ```

  

## 其他

```
修改布局为7行8列
defaults write com.apple.dock springboard-columns -int 8; defaults write com.apple.dock springboard-rows -int 7; defaults write com.apple.dock ResetLaunchPad -bool TRUE; killall Dock

修改背景图模糊 其中100代表程度，范围为0~255
defaults write com.apple.dock springboard-blur-radius -int 100; killall Dock

在Finder标题栏显示完整路径
defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
defaults delete com.apple.finder _FXShowPosixPathInTitle;killall Finder

killall Finder
从个人账户开始后面的路径 去掉Macintosh HD +用户
defaults write com.apple.finder PathBarRootAtHome -bool TRUE;killall Finder
defaults delete com.apple.finder PathBarRootAtHome;killall Finder
```

```
Visual Studio Code
SwitchHosts
Dash 
Alfred
Charles
SourceTree 
Sketch 
Skitch 
Virtual Box
QQ 
WeChat 
Airmail
IINA
ScreenFlow
Typora
The Unarchiver
Paste
Bartender
AppCleaner
iStat Menus
Moom  
ForkLift
```

[Git Awesome Mac](https://github.com/jaywcjlove/awesome-mac/blob/master/README-zh.md)

[MadreainNote](https://github.com/madreain/MadreainNote/blob/master/Mac/Mac-zh.md)

https://sspai.com/search/article?q=automa

[优雅使用macOS](https://www.zhihu.com/question/20873070) 

[alfred workflows](https://github.com/zenorocha/alfred-workflows)
https://www.zhihu.com/question/20656680

[快速查看插件](https://github.com/sindresorhus/quick-look-plugins)  

https://www.jianshu.com/p/253cb9003411  npm镜像

