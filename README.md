## MacOs: install and config Vagrant & VirtualBox using brew.

<p align="center">
  <img src="https://blog.octo.com/wp-content/uploads/2015/10/vagrant.jpg">
</p>

Vagrant is a tool for building and managing virtual machine environments in a single workflow. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases production parity, and makes the "works on my machine" excuse a relic of the past.

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

  _6.3_) If you encounter another error like this `Error: Kernel.exit` during execution, go to Settings & Privacy in your configs in Mac, and allow Oracle Extension. And repeat step #6.2 see [here](https://developer.apple.com/library/archive/technotes/tn2459/_index.html), otherwise just pass.
  
**7)** Remove any older versions from the cellar
`$ brew cleanup`

**8)** Now add the Vagrant box you want to use. See more infos about Boxes [here](https://www.vagrantup.com/intro/getting-started/boxes.html) 
I used Windows 10 with visual studio 2015 (see box [here](senglin/win-10-enterprise-vs2015community)), you can use some version of Ubuntu ([hashicorp/precise64](https://app.vagrantup.com/hashicorp/boxes/precise64))or any other, following the same path.

```console
$ vagrant box add senglin/win-10-enterprise-vs2015community
```

You can find more boxes at Vagrant Cloud. 
Now create a test directory and cd into the test directory. Then we'll initialize the vagrant machine.

```
$ vagrant init win-10-enterprise-vs2015community
```

### Up And SSH
It is time to boot your first Vagrant environment. Now lets start the machine using the following command from your terminal:

```console
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'senglin/win-10-enterprise-vs2015community' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: 1.0.0
==> default: Loading metadata for box 'senglin/win-10-enterprise-vs2015community'
    default: URL: https://vagrantcloud.com/senglin/win-10-enterprise-vs2015community
==> default: Adding box 'senglin/win-10-enterprise-vs2015community' (v1.0.0) for provider: virtualbox
    default: Downloading: https://vagrantcloud.com/senglin/boxes/win-10-enterprise-vs2015community/versions/1.0.0/providers/virtualbox.box
==> default: Box download is resuming from prior download progress
    default: Download redirected to host: vagrantcloud-files-production.s3.amazonaws.com
==> default: Successfully added box 'senglin/win-10-enterprise-vs2015community' (v1.0.0) for 'virtualbox'!
==> default: Importing base box 'senglin/win-10-enterprise-vs2015community'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'senglin/win-10-enterprise-vs2015community' version '1.0.0' is up to date...
==> default: Setting the name of the VM: mirian_default_1586431978800_50181
Vagrant is currently configured to create VirtualBox synced folders with
the `SharedFoldersEnableSymlinksCreate` option enabled. If the Vagrant
guest is not trusted, you may want to disable this option. For more
information on this option, please refer to the VirtualBox manual:

  https://www.virtualbox.org/manual/ch04.html#sharedfolders

This option can be disabled globally with an environment variable:

  VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

or on a per folder basis within the Vagrantfile:

  config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 3389 (guest) => 3389 (host) (adapter 1)
    default: 22 (guest) => 2222 (host) (adapter 1)
    default: 5985 (guest) => 55985 (host) (adapter 1)
    default: 5986 (guest) => 55986 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: WinRM address: 127.0.0.1:55985
    default: WinRM username: vagrant
    default: WinRM execution_time_limit: PT2H
    default: WinRM transport: negotiate
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default: 
    default: Guest Additions Version: 5.0.4
    default: VirtualBox Version: 6.1
==> default: Mounting shared folders...
    default: /vagrant => /Users/username
```

You can ssh into the machine now.

```console
$ vagrant ssh
```

Halt the vagrant machine now.
```console
$ vagrant halt

==> default: Attempting graceful shutdown of VM...
==> default: Forcing shutdown of VM...
```

Now go ahead and open up the VirtualBox application. You will see running. VirtualBox is letting us know that you box is running properly. 
