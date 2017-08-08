#### Vagrant LAMP Wordpress Environment

Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

Install [Vagrant](https://www.vagrantup.com/docs/installation/)

Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) [For Window](https://git-scm.com/download/win)

Clone the [Scotch Box GitHub Repository](https://box.scotch.io/)
```
git clone https://github.com/scotch-io/scotch-box.git lamp
```

Replace the __Vagrantfile__ inside the __lamp__ directory with the one from this repository, and edit as necessary.

Inside the directory that contains the __Vagrantfile__ run `vagrant up` to provision your LAMP environment.

After the provisioning is complete you will see that directories corresponding to the sites you added to the __Vagrantfile__ were created inside the __lamp__ directory.

Clone [Wordpress](https://wordpress.org/) inside the __public__ directory of of whatever site (domain) you want to work on.
Name the Wordpress directroy accordingly.
```
git clone https://github.com/WordPress/WordPress.git news
```

Inside the newly cloned Wordpress directory rename the __wp-config-sample.php__ to __wp-config.php__

Edit the __wp-config.php__ file to use the environment variables set up in the __Vagrantfile__.
Leave the default values for the secret keys.
```php
/* The name of the database for WordPress */
define('DB_NAME', getenv('DB_NAME_NEWS'));
/* MySQL database username */
define('DB_USER', getenv('DB_USER_NEWS'));
/* MySQL database password */
define('DB_PASSWORD', getenv('DB_PASSWORD_NEWS'));
/* MySQL hostname */
define('DB_HOST', getenv('DB_HOST_NEWS'));
```

Delete the __wp-content__ directory and replace it with the repo containing the sites customization as follows:
```
git clone git@codehub.esri.com:IST-Apps/Wordpress-Newsroom.git wp-content
```

Follow the instructions of the site's customization repository.

