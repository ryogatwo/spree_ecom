# SEE MY NOTES BELOW FOR INSTALL

---
---
---


# Spree Starter

This is a starter kit for [Spree Commerce](https://spreecommerce.org) - the open-source e-commerce platform for Rails. It is a great starting point for any Rails developer to quickly build an e-commerce store.

This starter uses:

* Spree Commerce 4.8 which includes Admin Dashboard, API and Storefront
* Ruby 3.3 and Ruby on Rails 7.1
* Solid Queue with Mission Control UI (access only to Spree admins) for background jobs
* Solid Cache for excellent caching and performance

You don't need to install any additional tools or libraries to start developing with Spree Starter. Everything is already set up for you.

## Installation

Make sure you have the following installed:
* Docker with Docker Compose - [installation instructions](https://docs.docker.com/get-docker/)
* Ruby 3.3 - [installation instructions](https://www.ruby-lang.org/en/documentation/installation/)
* Vips - [installation instructions](https://libvips.github.io/libvips/install.html)

```bash
bin/setup
```

If you want to use sample data (products, categories), you can load it using the following command:

```bash
bin/rake spree_sample:load
```

### Switching to MySQL

By default, Spree Starter uses PostgreSQL. If you want to switch to MySQL, you can do so by running the following command:

```bash
bin/rails db:system:change --to=mysql
```

You will also need to run `bin/setup` again to install the MySQL adapter and create the database.

### Launch local server

```bash
bin/rails s
```

## Deployment

### Using Render

<a href="https://render.com/deploy?repo=https://github.com/spree/spree_starter/tree/main">
  <img src="https://render.com/images/deploy-to-render-button.svg" alt="Deploy to Render" height=32>
</a>

Note that sample data does not automatically get loaded when deploying to Render with the default configuration. In order to add sample data, run the following commands in the web service shell:

```bash
bin/rake spree_sample:load
```

### Using Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### Other platforms

Spree Starter is a standard Rails application, so you can deploy it to any platform that supports Ruby on Rails applications. You can also use Docker to deploy it to any container-based platform. Please check [Spree Guides](https://guides.spreecommerce.org/developer/deployment.html) for more information.

## Troubleshooting

### libvips error

If you encounter an error like the following:

```bash
LoadError: Could not open library 'vips.so.42'
```

Please check that libvips is installed with `vips -v`, and if it is not installed, follow [installation instructions here](https://www.libvips.org/install.html).

___
___
___


# MY NOTES ON INSTALLING

** install spreecommerce on ubuntu  [ubuntu-22.04.2-live-server-amd64.iso]  **

(from: https://docs.spreecommerce.org/developer/getting-started/quickstart#setting-up-your-development-environment)


## * optional network tools 

>disable Cloud-Init 

```bash
sudo touch /etc/cloud/cloud-init.disabled
```

> network tools

```bash
sudo apt-get install cockpit net-tools btop neofetch
```

> to modify network settings (static ip, etc.) see:
> https://linuxconfig.org/setting-a-static-ip-address-in-ubuntu-24-04-via-the-command-line

> Optional stuff

```bash
neofetch
```

```bash
sudo snap install ponysay
```
```bash
export PATH=$PATH:/snap/bin
```

## * install dependencies 

```bash
sudo apt-get install software-properties-common libyaml-dev libpq-dev nodejs libvips libvips-tools git nano
```


## * install docker engine

### Add Docker's official GPG key:

```bash
sudo apt-get update
```
```bash
sudo apt-get install ca-certificates curl
```
```bash
sudo install -m 0755 -d /etc/apt/keyrings
```
```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Add the repository to Apt sources:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt-get update
```

> should show download.docker.com in the list from the command above


## * install docker

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose
```

> verify install

```bash
sudo docker run hello-world
```

## * install docker-desktop

### setup gnome for docker-desktop

```bash
sudo apt install gnome-terminal
```

### setup for docker-desktop

> The latest Ubuntu 24.04 LTS is not yet supported on docker-desktop
>
> (from :https://docs.docker.com/desktop/install/ubuntu/)

```bash
wget https://desktop.docker.com/linux/main/amd64/157355/docker-desktop-amd64.deb
```
```bash
sudo apt-get update
```
```bash
sudo apt-get install ./docker-desktop-amd64.deb
```
```bash
systemctl --user start docker-desktop
```


> Note:
>
> At the end of the installation process, apt displays an error due to installing a downloaded package. You can ignore this error message.
>
> N: Download is performed unsandboxed as root, as file '/home/user/Downloads/docker-desktop.deb' 
> couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)


### enable Docker Desktop to start on sign in,

```bash
systemctl --user enable docker-desktop
```


## * install imagemagick 

```bash
sudo apt-get install imagemagick libmagickwand-dev
```

> verify install

```bash
convert -version
```

## * install ruby 

```bash
sudo apt-get install ruby-full ruby-bundler ruby-railties rbenv
```

```bash
sudo gem install fileutils
```

```bash
sudo gem install bundler
```

```bash
sudo gem install rails
```

```bash
sudo gem install rmagick
```

> verify install

```bash
ruby --version
```

> used for ruby on rails

```bash
sudo apt-get install sqlite3
```

> test

```bash
sqlite3 --version
```

## * create your repo own cloned repo 

> goto this link on how to: <br>
> https://docs.spreecommerce.org/developer/getting-started/quickstart#creating-your-spree-repository <br>

> download using my cloned repo :

```bash
git clone https://github.com/ryogatwo/spree_ecom
```

> go into dir just dowloaded from git

```bash
cd ~/spree_ecom/
```
```bash
rails --version
```
> edit file (change in file to 3.0.2 or what shows up in version above and save)

```bash
nano .ruby-version       
```

>note: <br>
>
> - installed ---- rails 7.1.3.4 <br>
> - installed ---- ruby 3.0.2p107 <br>

## * install spree-ecom

```bash
sudo bundle install
```

```bash
sudo ./bin/setup
```

> add sample data to spree  (optional)

```bash
sudo rake spree_sample:load
```

### startup spree

```bash
sudo ./bin/rails s --binding=0.0.0.0
```


## * test

http://localhost:3000/admin

> (if used defaults)
> user (admin) = spree@example.com
> pass = spree123


http://localhost:3000/

> DONE!

```bash
ponysay --pony trixie  'Ta DA !'
```



