# Basic lamp role

[![Build Status](https://travis-ci.org/softasap/sa-lamp.svg?branch=master)](https://travis-ci.org/softasap/sa-lamp)


# Background


## Challenges to address
  * Optionally install MySQL (you might use external database)
  * Install Lamp  

Let's go step by step.



## Describing desired components

Let's list both package dependencies and needed php extensions.
<pre>
  pkg_dependencies:
    - git
    - curl
    - python-dev
    - libmysqlclient-dev

  php_extensions:
    - php5-mysql
    - php5-intl
    - php5-xmlrpc
    - php5-curl
    - php5-gd
</pre>


## Optional MySQL installation

In order to install MySQl, you will need to specify desired mysql root credentials only.
<pre>
  mysql_host: "127.0.0.1"
  mysql_root_user: root
  mysql_root_password: SOMEROOTSECUREPASSWORD
</pre>


## LAMP installation
For LAMP we have ability to install apache either in worker or prefork mode.
This has impact on PHP: it will be installed either as PHP-FPM or via mod_php apache module.
Nowadays worker is preferable.
<pre>
  apache_mode: worker # use prefork or worker variables
  apache2_disable_default: true

  php_family: default # 5.4 | 5.5 | 5.6 | default
</pre>



## Usage example

<pre>

     - {
         role: "sa-lamp",
         option_install_mysql: false
       }


</pre>
