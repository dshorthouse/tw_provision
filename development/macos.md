TaxonWorks development environment for MacOS X 
==============================================
Overview
--------
1. Assumes a clean install of the OS.
2. Copy and paste each line, this is not intended to run as a shell script.
3. Carefully read the instructions before each line before exectuting the line.

Instructions
------------

Open a terminal.

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
When or if prompted click on install button.

Follow through Homebrew

```
brew install gnupg

gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
```
\curl -sSL https://get.rvm.io | bash -s stable --ruby

brew install postgres

brew install postgis 

brew install imagemagick

brew install cmake

mkdir -p ~/Library/LaunchAgents    # This may already exist.   

ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents

launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

mkdir Projects

git clone https://github.com/SpeciesFileGroup/taxonworks.git
```

cd taxonworks

 You may see a message regarding a particular version of Ruby.  Install that version of Ruby with the command provided in the terminal  It will look something like:

#   rvm install 2.1.5

bundle

createuser -s -d -P taxonworks_development # Supply a password or just press return twice for no password.

cp config/database.yml.example config/database.yml # If you supplied a password in the previous step please edit database.yml accordingly.

rake db:create

# If you see an error regarding Proj4 please run the next 3 commands, otherwise skip them

# gem uninstall rgeo

# gem install rgeo

# rake db:create

# Install Firefox browser if you don’t have it yet.

rake db:migrate && rake db:test:prepare