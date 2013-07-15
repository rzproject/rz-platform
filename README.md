rz-platform
===========

Base Symfony2 Application with SotanaBundles and RzBundles

What's inside?
--------------

rz-platform a base platform is based on Sonata and RzProject AdminBundle.


Installation from Sonata Sandbox
--------------------------------

Run the following commands::

    git clone https://github.com/rzproject/rz-platform rz-platform
    cd rz-platform
    rm -rf .git
    git init
    git add .gitignore *
    git commit -m "Initial commit (from the Sonata Sandbox)"
    php bin/vendors install
    git add *
    git commit -m "add submodules"
    cp app/config/parameters.yml.sample app/config/parameters.yml
    cp app/config/parameters.yml.sample app/config/validation_parameters.yml
    cp app/config/parameters.yml.sample app/config/production_parameters.yml

.. note::

  The ``bin/vendor`` script does not behave like the one provided by the Symfony2 Standard Edition.
  The script install vendors as git submodules.


Database initialization
-----------------------

At this point, the ``app/console`` command should start with no issues. However some you need the complete some others step:

* database configuration (edit the app/config/parameters.yml file)

then runs the commands::

    app/console doctrine:database:create
    app/console doctrine:schema:create

Fixtures (For Demo Purpose Only)
--------------------------------

To have some actual data in your DB, you should load the fixtures by running::

    app/console doctrine:fixtures:load


Assets Installation
-------------------

Your frontend still looking weird because bundle assets are not installed. Run the following command to install assets for all active bundles under public directory::

    app/console assets:install web


Create User
-----------

.. note::

    Only execute if you not loading fixtures

Create User::

    php app/console fos:user:create admin youremail@example.com admin

Add Role::

    php app/console fos:user:promote admin ROLE_SUPER_ADMIN


Unit Testing
------------

Automatic Unit Testing with ``watchr``::

    gem install watchr
    cd /path/to/symfony-project
    watchr phpunit.watchr



Enjoy!

A Fork from Sonata Sandbox https://github.com/sonata-project/sandbox
