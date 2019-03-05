# LaraBlog

A [LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) stack WordPress clone using [Laravel](https://laravel.com).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

You will need the following installed on your local machine:

* [A computer with Virutalization capabilities](https://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/). If you do not have one, then you will need to install all development software on your personal computer instead of using the virtualization software.
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) - Virtualization software
* [Vagrant](https://www.vagrantup.com/intro/getting-started/install.html) - Used to make VirtualBox setup easier for web development
* [Vagrant Hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater) - Used for automatically updating your local machine's hostfile.
* [PHP](https://windows.php.net/download) - Used for code completion/correction within VS Code ****_optional_**
* [VS Code](https://code.visualstudio.com/download) - Code editor ****_optional_**

Helpful packages for VS Code (can be installed within VS Code):

* [Apache Conf](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-apache) - Syntax highlighing for Apache conf files in Visual Studio Code.
* [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag) - Automatically add HTML/XML close tag, same as Visual Studio IDE or Sublime Text does.
* [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag) - Automatically rename paired HTML/XML tag, same as Visual Studio IDE does.
* [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) - ENV file syntax highlighting.
* [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - GitLens supercharges the Git capabilities built into Visual Studio Code.
* [Laravel Blade Snippets](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade) - Laravel blade snippets and syntax highlight support for Visual Studio Code.
* [Laravel Helpers](https://marketplace.visualstudio.com/items?itemName=rafa-acioly.laravel-helpers) - A set of Laravel Snippets for Visual Studio Code.
* [Open file From Path](https://marketplace.visualstudio.com/items?itemName=jack89ita.open-file-from-path) - Simple plugin for VS Code that allows you to quickly open file starting from path string.
* [phpfmt - PHP formatter](https://marketplace.visualstudio.com/items?itemName=kokororin.vscode-phpfmt) - The missing phpfmt extension for Visual Studio Code.
* [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client) - PHP IntelliSense.
* [PHP Namespace Resolver](https://github.com/MehediDracula/PHP-Namespace-Resolver) - PHP Namespace Resolver can import and expand your class. You can also sort your imported classes by line length or in alphabetical order.
* [phpfmt - PHP formatter](https://marketplace.visualstudio.com/items?itemName=kokororin.vscode-phpfmt) - The missing phpfmt extension for Visual Studio Code.
* [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight) - Highlight TODO, FIXME and other annotations within your code.

Helpful Tweak of VS Code:

1. Go to File -> Preferences -> Settings.
2. Within the new window, click on Text Editor -> Formatting.
3. Check Format on Paste (and possibly other options if you would like)

### Installing

* Follow [this guide](https://medium.com/@eaimanshoshi/i-am-going-to-write-down-step-by-step-procedure-to-setup-homestead-for-laravel-5-2-17491a423aa) to get Laravel Homestead installed on your machine. It is written for Laravel 5.2, but it works up to 5.8 so far.
  * In step 3, you do NOT need Git Bash. You can run all commands through normal CMD.
  * In step 5, instead of using `cd ~`, you can open File Explorer and navigate to the directory where you want your projects installed. For example, `C:\Users\Ryan\Desktop\projects\` and then copy the directory and type `cd [PASTED DIRECTORY]`. If you do not want to download Git on your local machine, then where it says to type `git clone https://github.com/laravel/homestead.git Homestead`, instead, just click the link and then directly download the zip file from GitHub and unzip it into your preferred directory. Then when it says to type `bash init.sh`, you can just double click on the `init.bat` within your File Explorer as well.
  * In Step 7, map the site to larablog.local or something similar ([do NOT use .dev extension](https://ma.ttias.be/chrome-force-dev-domains-https-via-preloaded-hsts/)). I also just add an `apps` directory within the Homestead folder, so the `folders` portion of my Homestead.yaml file looks like this:

  ```batch
    ...

    folders:
    — map: c:/Users/Ryan/Desktop/projects/homestead/apps/
    to: /home/vagrant/code

    sites:
    - map: larablog.test
      to: /home/vagrant/code/larablog/public

    ...
  ```

  * **Stop reading the tutorial once you finish Step 7.**
* Launch vagrant (this will take a while for the first time)
  * Open cmd in Administrator mode
    * If you installed VS Code, then launch it in Administrator mode instead. Go to Terminal -> New Terminal in the menu bar. No need for an extra cmd window!
  * Open the directory for the development environment
  * Type: `vagrant up`
    * Note: to stop vagrant from runnning, type: `vagrant halt`
* Once Vagrant is done setting up, type: `vagrant ssh`
* Change into your `code` directory within your ssh terminal
* Log into GitHub, locate the LaraBlog repo and click 'Clone or download' and copy the URL.
* Use these commands within your terminal:

  ```batch
  mkdir larablog
  cd larablog
  git init
  git remote add origin [URL COPIED FROM GITHUB]
  git fetch && git checkout dev
  git pull
  sudo mv .env.example .env
  composer install
  php artisan key:generate
  php artisan migrate
  php artisan db:seed
  ```

* You can now open your preferred code editor and edit the files within your shared directory and access your changes live at the URL you specified within your preferred web browser. Make sure you have Vagrant Hosts Updater plugin installed so that you do not have to update your hostfile manually.
* Note that sometimes VS Code does not register file changes or the 'Source Control' acts weird. If you exit out of VS Code and re-open it as Administrator, it will work fine. As far as I can tell, this is a random bug.

## Documentation and Help

All technologies used in this project are popular, so there's a good chance that what you're looking for is on [Google](https://www.google.com).
Although, here is a consolidated list of resources to help anyone get started with this project:

* [Official Laravel Docs](https://laravel.com/docs/5.7/)
* [Laravel Help Forum](https://laracasts.com/discuss)
* [Official PHP Docs](http://php.net/docs.php)
* [Blade Templating Engine Docs](https://laravel.com/docs/master/blade)
* [MDN Javascript Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
* [Official Bootstrap Docs](https://getbootstrap.com/docs/4.1/layout/overview/)
* [Learn Sass](https://sass-lang.com/guide)
* [JQuery API](https://api.jquery.com/)
* [Official Vue.js Docs](https://vuejs.org/v2/guide/)
* [Laravel General Cheat Sheet](https://learninglaravel.net/cheatsheet/)
* [Vagrant Commands Cheat Sheet](https://gist.github.com/wpscholar/a49594e2e2b918f4d0c4)
* [Linux Commands Cheat Sheet](https://www.linuxtrainingacademy.com/linux-commands-cheat-sheet/)
* [Markdown Cheat Sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

## Versioning

Given a version number **MAJOR.MINOR.PATCH**, increment the:

1. MAJOR version when you make incompatible API changes,
2. MINOR version when you add functionality in a backwards-compatible manner, and
3. PATCH version when you make backwards-compatible bug fixes.

Additional labels for pre-release are available as extensions to the **MAJOR.MINOR.PATCH** format.

* **alpha**: Pre-release or still in development code
  * Example: **1.12.1-alpha**
* **beta**: Pre-release code that is being tested
  * Example: **1.12.1-beta**

For more information you may visit [SemVer](http://semver.org/).

## Authors

* **[Ryan Huett](https://github.com/im-ryan)** - Project Lead

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details.