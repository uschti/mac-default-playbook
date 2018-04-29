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

  - [Dropbox](https://www.dropbox.com/)
  - [Firefox](https://www.mozilla.org/en-US/firefox/new/)
  - [Google Chrome](https://www.google.com/chrome/)
  - [Handbrake](https://handbrake.fr/)
  - [Homebrew](http://brew.sh/)

Packages (installed with Homebrew):

  - git
  - gpg
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
