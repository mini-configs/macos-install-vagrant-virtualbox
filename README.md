# macos-install-vagrant-virtualbox
How install Vagrant and Virtual box using brew

### Install Vagrant
Vagrant uses Virtualbox to manage the virtual dependencies 

**1) Update Brew**
``` console
$ brew update              
Updated 2 taps (homebrew/core and homebrew/cask).
==> Updated Formulae
broot               newman              serverless          syncthing
==> Updated Casks
keyshot             pdfelement          pycharm             pycharm-ce
```

**2) Install vagrant**
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

**3) Install vagrant-manager**
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

**4) Searches all known Casks for a partial or exact match**
`$ brew search virtualbox`

**5) Displays information about the given Cask**
` $ brew cask info virtualbox`

**6) Install the given cask - virtualbox**
`$ brew cask install virtualbox`

  _6.1_) If return an error like the one below. This is a macOS issue because of secure kext loading in High Sierra.
```console
Error: Failure while executing; 
...

Here's the output:
installer: Package name is Oracle VM VirtualBox
```

  _6.2_) So, try this and will work: 
```console
$ brew cask reinstall --force virtualbox --verbose --debug
```

  _6.3_) If you encounter another error like this, during execution:
`Error: Kernel.exit`

  _6.4_) Go to Settings & Privacy in your configs in Mac, and allow Oracle Extension. And repeat step #6.2 See this: [here](https://developer.apple.com/library/archive/technotes/tn2459/_index.html)
  
**7)** Remove any older versions from the cellar
`$ brew cleanup`

