# macos-install-vagrant-virtualbox
How install Vagrant and Virtual box using brew

### Install Vagrant
Vagrant uses Virtualbox to manage the virtual dependencies 

``` console
$ brew update              
Updated 2 taps (homebrew/core and homebrew/cask).
==> Updated Formulae
broot               newman              serverless          syncthing
==> Updated Casks
keyshot             pdfelement          pycharm             pycharm-ce
```

``` console
$ brew cask install vagrant   
==> Downloading https://releases.hashicorp.com/vagrant/2.2.7/vagrant_2.2.7_x86_6
######################################################################## 100.0%
==> Verifying SHA-256 checksum for Cask 'vagrant'.
==> Installing Cask vagrant
==> Running installer for vagrant; your password may be necessary.
==> Package installers may write to any location; options such as --appdir are i
Password:
installer: Package name is Vagrant
installer: Installing at base path /
installer: The install was successful.
🍺  vagrant was successfully installed!
```

```console
$ brew cask install vagrant-manager
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/cask).
==> Updated Casks
alt-tab                                  segger-embedded-studio-for-arm

==> Downloading https://github.com/lanayotech/vagrant-manager/releases/download/
==> Downloading from https://github-production-release-asset-2e65be.s3.amazonaws
######################################################################## 100.0%
==> Verifying SHA-256 checksum for Cask 'vagrant-manager'.
==> Installing Cask vagrant-manager
==> Moving App 'Vagrant Manager.app' to '/Applications/Vagrant Manager.app'.
🍺  vagrant-manager was successfully installed!
```

```
