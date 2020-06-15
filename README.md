# DQS Site

**The source code for the DQS jekyll-based info and docs site.**

## Dev Environment

Here's how to set up a dev env for the DQS site on various platforms:

### Installing Ruby & Jekyll

First thing's first; you'll need to install Ruby, cos the site is Jekyll-based, and Jekyll is itself a Ruby gem.

#### Windows

Windows isn't officially supported by Jekyll though, so be warned. We'll need to do some tweaking.

Firstly, you'll need to get **RubyInstaller**, the preferred method of installing ruby on windows, [here](https://rubyinstaller.org/downloads/). Be sure to get the 'with devkit' version for either 32 or 64 bit, depending on your system.

On the last stage of the installation, run the `ridk install` bit of the installation, which is required for Jekyll's native extensions.

Once that's done, open a command prompt from the start menu and install Jekyll and Bundler, with this command: `gem install jekyll bundler`.

To verify the installation, try `jekyll -v`. A restart may be required.

#### Ubuntu Linux

Firstly, run this command to get all dependencies:

```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Cos installing gems to the root user is a bit gay, you'll want to run these commands to get yourself a gem install path for your user account.

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Once that's all done, install Jekyll and Bundler like so: `gem install jekyll bundler`.

#### macOS

First, you'll need to install the command line tools. Open a terminal and run: `xcode-select --install`.

Jekyll requires Ruby version 2.5.0 or newer to run. Ruby 2.6.3 comes included with macOS Catalina, so if you have that, you can skip the installing Ruby bits.

If you don't have Catalina, use homebrew like so to install Ruby:

```bash
# Install Homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install ruby
```

Then add the brew ruby path to your sh config:

```bash
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile
```

Relaunch your terminal and run `ruby -v` to verify your installation.

Now you just have to install Jekyll, like so:

```bash
gem install --user-install bundler jekyll
```

### Project Setup

Firstly, clone the project either with SSH or HTML into a directory of your choosing.

SSH (Recommended):

```bash
git clone git@gitlab.com:dewysoftware/documentation/dqs-site.git
```

HTML:

```bash
git clone https://gitlab.com/dewysoftware/documentation/dqs-site.git
```

You can then simply open the folder in a text editor or IDE of your choosing. For instance, with IntelliGay, just open the folder from the main menu.

Then, from there, you can cd into the project directory and run

```bash
jekyll s
```

to start the server on port **4000**.