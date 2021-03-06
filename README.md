# Basic lamp role (archived, splitted into separate roles)

[![Build Status](https://travis-ci.org/softasap/sa-lamp.svg?branch=master)](https://travis-ci.org/softasap/sa-lamp)


# Update Dec 2018

Actually, this role is combination of `sa-mysql`, `sa-apache`, `sa-apache-php`.
Also, if you are looking into php in fpm mode, that might want to look into `sa-nginx` and `sa-php-fpm`. 

# Background


## Challenges to address
  * Optionally install MySQL (you might use external database)
  * Install Lamp  

Let's go step by step.



## Describing desired components

Let's list both package dependencies and needed php extensions.
```YAML
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
```


## Optional MySQL installation

In order to install MySQl, you will need to specify desired mysql root credentials only.
```YAML
  mysql_host: "127.0.0.1"
  mysql_root_user: root
  mysql_root_password: SOMEROOTSECUREPASSWORD
```


## LAMP installation
For LAMP we have ability to install apache either in worker or prefork mode.
This has impact on PHP: it will be installed either as PHP-FPM or via mod_php apache module.
Nowadays worker is preferable.
```YAML
  apache_mode: worker # use prefork or worker variables
  apache2_disable_default: true

  php_family: default # 5.4 | 5.5 | 5.6 | 7.0 | default
```



## Usage example

```YAML

     - {
         role: "sa-lamp",
         option_install_mysql: false
       }


```


### Version History

1.4.0  In OAndrey repo used, the oldest php supported is 5.6 now
1.3.0  (cosmetic) Fixed mess with tags in meta
1.2.0  Support for ansible 2.0 syntax ; Introduced tests for 16.04


Usage with ansible galaxy workflow
----------------------------------

If you installed the sa-lamp role using the command


`
   ansible-galaxy install softasap.sa-lamp
`

the role will be available in the folder library/softasap.sa-lamp
Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-lamp"
       }

```


Copyright and license
---------------------

Code is dual licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) and the [MIT License] (http://opensource.org/licenses/MIT). Choose the one that suits you best.

Reach us:

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)

Join gitter discussion channel at [Gitter](https://gitter.im/softasap)

Discover other roles at  http://www.softasap.com/roles/registry_generated.html

visit our blog at http://www.softasap.com/blog/archive.html
