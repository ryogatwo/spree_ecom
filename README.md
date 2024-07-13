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

-------------------------------------------
-------------------------------------------
-------------------------------------------

### My notes on installing ###

** install spreecommerce on ubuntu Ubuntu 22.04.4 LTS x86_64 **

(from: https://docs.spreecommerce.org/developer/getting-started/quickstart#setting-up-your-development-environment)


### optional network tools ###

sudo apt-get install cockpit net-tools btop neofetch



### install dependencies ###

sudo apt-get install software-properties-common libyaml-dev libpq-dev nodejs libvips libvips-tools



### install imagemagick  ###

sudo apt-get install imagemagick libmagickwand-dev

# test with

convert -version



### install ruby ###

sudo apt-get install ruby-full ruby-bundler ruby-railties rbenv

ruby --version

sudo gem install fileutils

# sudo gem install rails   !!!! dont think this is needed !!!

sudo gem install bundler



### install docker engine ###

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose docker-desktop

# test with

sudo docker run hello-world



### clone your repo (see top web link for howto) ###

# setup using my cloned repo

git clone https://github.com/ryogatwo/spree_ecom

# go into dir just dowloaded from git

cd ~/spree_ecom/

ruby --version

# edit file 

nano .ruby-version       (change in file to 3.0.2 or what shows up in version above and save)

# install spree-ecom

sudo ./bin/setup

# add sample data to spree  (optional)

sudo rake spree_sample:load

# startup spree

sudo ./bin/rails s --binding=0.0.0.0



### test ###

http://localhost:3000/admin


(if used defaults)
user (admin) = spree@example.com
pass = spree123


http://localhost:3000/







