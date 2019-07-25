References:
https://github.com/sb2nov/mac-setup
http://brew.sh/
https://github.com/rbenv/rbenv
https://wiki.postgresql.org/wiki/Homebrew
https://sourabhbajaj.com/mac-setup/Git/

1. Open Terminal.

1b. Create and enter our working directory:
mkdir Workspace
cd Workspace
mkdir solidus-workshop
cd solidus-workshop

2. Install X-Code (if you haven't already):

```bash
xcode-select --install
```

Optional: check if system ruby is already installed (it should be):
```bash
ruby -v
```

3. Install Homebrew:

(check for previous installation with `brew doctor`)

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
(And make sure it, homebrew's executable directory (/usr/local/bin) has added to your path)

4. Now go for a checkup at the doctor's with:
```bash
brew doctor
```
(And fix anything it complains about, possible `brew update`)

5. Install rbenv:

(check for previous installation with `rbenv -v`; optional upgrade for those already with rbenv installed `brew upgrade rbenv ruby-build`)

```bash
brew install rbenv
```

(note: this also installs `ruby-build`)

And initialize it:

```bash
  rbenv init
```

And then check to see it's properly installed:
```bash
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```

rbenv init

echo 'eval "$(rbenv init -)"' >> ~/.bash_profile

6. Install Ruby:
Check available versions:
```bash
rbenv install -l
```
Install your selected version, and set it:
```bash
rbenv install 2.4.6

rbenv local 2.4.6
```

7. Install git, check the version, and set your name and email:
```bash
brew install git

git --version

git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"
```

8. Install postgres:
brew install postgresql
brew services start postgresql
pgsql postgres #to login

9. Install Imagemagick:

```bash
brew install imagemagick
```

gem install bundler

gem update --system

gem install rails
OR
gem install rails -v '5.2.3' -V --no-ri --no-rdoc

10. Create a new Rails app
rails new my-solidus-website --database=postgresql
OR
rails _5.2.3_ new my-solidus-website --database=postgresql

11. Add Solidus gems

```
gem 'solidus', '~> 2.5'

gem 'solidus_auth_devise'

gem 'deface'
```

End:

Run the final commands to finish setting up the Solidus Project:

bundle exec rails g spree:install

bundle exec rails g solidus:auth:install

bundle exec rake railties:install:migrations

bundle exec rake db:migrate

Start the server!

bundle exec rails s
