# Set Golang Development Environment on Mac OS X in China

## Tested Mac OS X Version
* 10.15.4 Catalina

## Testd Go Version
* 1.14.1

## Install Tools(Optional)
* [aria2](https://github.com/aria2/aria2)
  * [Install aria2 on Mac OS X](https://github.com/northbright/Notes/blob/master/aria2/install-aria2-on-mac-os-x.md)
    
## Download Latest Release of Go from <https://golang.google.cn/>
```
aria2c https://dl.google.com/go/go1.14.1.darwin-amd64.pkg
```

## Open the dmg and Install Go

## Check Go Version
```
go version
```
```
which go
// Output
/usr/local/go/bin/go
```

## Set Go Environment Variables
* `GOPROXY`
  * `go get` packages from `"https://golang.org/x/XX"` will fail in China(golang.org is blocked in China)
  * `GOPROXY` is  set to `"https://proxy.golang.org,direct"` by default
  * `"https://proxy.golang.org"` is blocked in China
  * Set `GOPROXY` to `"https://goproxy.io"` for gophers in China
* `GOSUMDB`
  * Set `GOSUMDB` to `"sum.golang.google.cn"` for gophers in China
* `GOPATH`
  * If you want to run the binary installed from `go get`(e.g. [staticcheck](https://staticcheck.io/)), we need to set `$GOPATH` and add `$GOPATH/bin` to `$PATH` in `~/.zprofile`

```
// Mac OS X 10.15 use zsh as default shell which use ~/.zprofile
vi ~/.zprofile
```
```
export GOPROXY="https://goproxy.io,direct"
export GOSUMDB="sum.golang.google.cn"
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```
```
// Reload `~/.zprofile` in current terminal
source ~/.zprofile
```

## Check Golang Environment Variables
```
go env

// Output:
...
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/local/go"
GOSUMDB="sum.golang.google.cn"
...
```

## Instal `vim-go` Plugin for Vim(Optional)
* [Use vim-plug to Install Vim Plugins on CentOS 7](https://github.com/northbright/Notes/blob/master/Linux/vim/use-vim-plug-to-install-vim-plugins.md)
* [Add vim-go Plugin for VIM on CentOS 7](https://github.com/northbright/Notes/blob/master/Golang/Editor/Add_vim-go_for_vim_on_CentOS_7.md)
The articles are also applied to Mac OS X. 

## Vim Settings
* [Make Vim Remember Last Position on Mac OS X](https://github.com/northbright/Notes/blob/master/Linux/vim/make-vim-remember-last-position-on-mac-os-x.md)


## Install and Configure Git(Optional)
* Install Git
```
xcode-select --install
```

* Configure `Git`

  ```
  git config --global user.email "xx@xx.com"
  git config --global user.name "My Name"
  git config --global color.ui true

  // Check
  git config --global -l
  ```

* Add New SSH Key and Add Public Key to Github Account
  ```
  ssh-keygen -t rsa -b 2048
  ```
  Copy the public key in `~/.ssh/id_rsa.pub` and go to [github SSH settings](https://github.com/settings/ssh) to add new SSH key.

## References
* [Go 1.14 Release Notes](https://golang.google.cn/doc/go1.14)
* [五分钟学会使用 go modules（含在家办公使用技巧）](https://gocn.vip/topics/9820)
* [干货满满的 Go Modules 和 goproxy.cn](https://gocn.vip/topics/9484)
* [Go Modules 终极入门](https://gocn.vip/topics/9904)
* [谈谈gomod/goproxy/gosumdb](https://zhuanlan.zhihu.com/p/111722890)
* <https://goproxy.io/>
* [Set alias on Mac OS X which its Default Shell is zsh](https://github.com/northbright/Notes/blob/master/macos/shell/set-alias-on-mac-os-x-which-default-shell-is-zsh.md)
