# Mac Default (normal usage) Ansible Playbook

This playbook installs and configures most of the software used in normal Mac (NOT DEV users, normal usage).

## Installation

  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
  2. [Install Ansible](http://docs.ansible.com/intro_installation.html).
  3. Clone this repository to your local drive.
  4. Run `$ ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  5. Run `ansible-playbook main.yml -i inventory -K` inside this directory. Enter your account password when prompted.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook`'s `--tags` flag. The tags available are `dotfiles`, `homebrew`, `mas`, `extra-packages` and `osx`.

    ansible-playbook main.yml -i inventory -K --tags "dotfiles,homebrew"

## Included Applications / Configuration (Default)

Applications (installed with Homebrew Cask):

  - [Avg] (https://www.avg.com/)
  - [Dropbox](https://www.dropbox.com/)
  - [Homebrew](http://brew.sh/)
  - [Adobe Acrobat Reader] (https://acrobat.adobe.com/ch/it/acrobat/pdf-reader.html)
  - [Caffeine] (https://caffeine.it.softonic.com/mac)
  - [Cyberduck] (https://cyberduck.io/)
  - [Dropbox] (https://www.dropbox.com/it/)
  - [Java 8] (http://www.oracle.com/)
  - [Firefox](https://www.mozilla.org/en-US/firefox/new/)
  - [Gimp] (https://www.gimp.org/)
  - [Google Chrome](https://www.google.com/chrome/)
  - [Google Earth Pro] (https://www.google.com/intl/it/earth/desktop/)
  - [Image 2 Icon] (http://www.img2icnsapp.com/)
  - [Istat Menus] (https://bjango.com/mac/istatmenus/)
  - [Libreoffice] (https://it.libreoffice.org/)
  - [Keepassxc] (https://keepassxc.org/)
  - [Keka] (http://www.kekaosx.com/)
  - [Synology Cloud Station] (https://www.synology.com/)
  - [Nextcloud] (https://nextcloud.com/)
  - [Skype] (https://www.skype.com/)
  - [Smcfancontrol] (https://smcfancontrol.it.uptodown.com/mac)
  - [Thunderbird] (https://www.thunderbird.net/)
  - [Tunnelblick] (https://tunnelblick.net/)
  - [Vmware Fusion] (https://www.vmware.com/products/fusion.html)
  - [Vlc] (https://www.videolan.org/)
  - [Whatsapp] (https://www.whatsapp.com/)
  - [Youtube to mp3] (https://www.mediahuman.com/it/youtube-to-mp3-converter/)

Packages (installed with Homebrew):

  - ffmpeg
  - git
  - gpg
  - openssl
  - wget

My [dotfiles](https://github.com/geerlingguy/dotfiles) are also installed into the current user's home directory, including the `.osx` dotfile for configuring many aspects of macOS for better performance and ease of use. You can disable dotfiles management by setting `configure_dotfiles: no` in your configuration.

Finally, there are a few other preferences and settings added on for various apps and services.

## Future additions

### Things that still need to be done manually

  1. Configure extra Mail and/or Calendar accounts (e.g. Google, Exchange, etc.).


## Testing the Playbook

Many people have asked me if I often wipe my entire workstation and start from scratch just to test changes to the playbook. Nope! Instead, I posted instructions for how I build a [Mac OS X VirtualBox VM](https://github.com/geerlingguy/mac-osx-virtualbox-vm), on which I can continually run and re-run this playbook to test changes and make sure things work correctly.

## Author

[Uschti], 2018 (originally inspired by [kisamoto/mac-dev-playbook](https://github.com/kisamoto/mac-dev-playbook)).
