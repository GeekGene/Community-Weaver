# Community Weaver 2.0 - Timebanking System from TimeBanksUSA

## Background
This is an open source template for running a timebank on Drupal. It was built by The Geek Gene for Time Banks USA as an upgrade to their previous timebanking system which ran on a BBS framework. Switching to a modern CMS provided many updated features and integrations for them, and also brought the project into the open source space.

This project is no longer maintained by The Geek Gene as Time Banks USA went back to a more proprietary approach, and works with a different software development company on their new version of the tools.

## Overview

This installation guide is intended for someone who knows Drupal and wants to install Community Weaver 2.0 on their own server.

Community Weaver 2.0 is based on Drupal 6; uses about 80 contributed Drupal modules, a few Drupal Supporting Libraries, and a Drupal theme. Additionally it uses 2 Drupal modules custom written for CW 2.0. The components developed for Community Weaver 2.0 are:

    the Time Banks Drupal Module - provides a number of customizations on top of existing contributed modules, Guardian Angel functionality, etc.
    the Availability Check Grid Module - creates a grid of checkboxes to show a user's general availability throughout the week
    the MYSQL template of the Drupal database for Community Weaver 2.0 - provides all the settings and configurations that make up a complete Community Weaver 2.0 website ready for new users, ads, transactions, and other content to be added

## Installation

The installation process includes the following 10 steps. (see below for details.)
  1. Install Drupal
  2. Install Current Versions of Contributed Modules
  3. Install Supporting Code Libraries
  4. Install the Required Theme
  5. Install Availability Check Grid module
  6. Install Time Banks module
  7. Load Community Weaver 2.0 database template
  8. Configure Various Community Weaver and Drupal System Components
  9. Configure Web Host Settings
  10. Configure Final Settings in Drupal

### 1. Install Drupal

Start with a fresh installation of drupal 6.x and install it as a multisite installation.  As of this writing the current version is 6.25.  Where this should be installed is highly dependent upon your host/server provider, but generally goes wherever index.html can be found.  It might be /var/www/html or ~/www or /public_html. A guide on drupal installation can be found here.  Download the compressed archive of drupal from http://drupal.org/project/drupal.  From the command line you can use the following, replacing the x with the appropriate version:

     wget http://ftp.drupal.org/files/projects/drupal-6.x.tar.gz

Uncompress the file into your working directory.  For the rest of this document this directory is referred to as Drupal_Home in brackets to remind you to replace it with your real [Drupal_Home] directory.  You could use:

     tar xzvf drupal-x.x.tar.gz

In the [Drupal_Home] directory, there will be a sites/ directory and a sites/default directory.  For multi-site usage, you'll need to create a sites/[YOURSITE].  YOURSITE refers to the url of your website such as mytimebankname.org or timebanksrock.net.  In that directory, you'll then need a settings.php that is copied from sites/default/default.settings.php and a /files directory.  So looking at [Drupal_Home]/sites/[YOURSITE] you should see:

    files/
    settings.php  

### 2. Install Current Versions of Contributed Modules

Then you'll also need the following contributed modules installed in [Drupal_Home]/sites/all/modules/ :

    http://drupal.org/project/admin_menu 
    http://drupal.org/project/advanced_help 
    http://drupal.org/project/auto_nodetitle 
    http://drupal.org/project/autoload
    http://drupal.org/project/ban_unpublish 
    http://drupal.org/project/better_formats 
    http://drupal.org/project/calendar 
    http://drupal.org/project/captcha 
    http://drupal.org/project/captcha_pack 
    http://drupal.org/project/cck 
    http://drupal.org/project/content_access 
    http://drupal.org/project/content_profile 
    http://drupal.org/project/content_taxonomy 
    http://drupal.org/project/ctools 
    http://drupal.org/project/custom_search 
    http://drupal.org/project/date 
    http://drupal.org/files/issues/datesort.zip
    http://drupal.org/project/devel 
    http://drupal.org/project/filefield 
    http://drupal.org/project/gmap 
    http://drupal.org/project/google_analytics 
    http://drupal.org/project/image 
    http://drupal.org/project/imageapi 
    http://drupal.org/project/imagecache 
    http://drupal.org/project/imagecache_profiles 
    http://drupal.org/project/imagefield 
    http://drupal.org/project/imce 
    http://drupal.org/project/imce_wysiwyg 
    http://drupal.org/project/jquery_ui 
    http://drupal.org/project/jstools 
    http://drupal.org/project/libraries 
    http://drupal.org/project/lineage 
    http://drupal.org/project/link 
    http://drupal.org/project/location 
    http://drupal.org/project/logintoboggan 
    http://drupal.org/project/me 
    http://drupal.org/project/menu_block 
    http://drupal.org/project/menu_breadcrumb 
    http://drupal.org/project/messaging 
    http://drupal.org/project/mimemail 
    http://drupal.org/project/mutual_credit (should use 6.x-2.5)
    http://drupal.org/project/nodeblock 
    http://drupal.org/project/node_expire 
    http://drupal.org/project/nodereference_url 
    http://drupal.org/project/panels 
    http://drupal.org/project/pathauto 
    http://drupal.org/project/persistent_login 
    http://drupal.org/project/phone 
    http://drupal.org/project/poormanscron 
    http://drupal.org/project/privatemsg 
    http://drupal.org/project/privatemsg_bulkmail 
    http://drupal.org/project/privatemsg_views 
    http://drupal.org/project/recaptcha 
    http://drupal.org/project/role_delegation 
    http://drupal.org/project/rules 
    http://drupal.org/project/securepages 
    http://drupal.org/project/services 
    http://drupal.org/project/services_oauth 
    http://drupal.org/project/skinr 
    http://drupal.org/project/stringoverrides 
    http://drupal.org/project/taxonomy_image 
    http://drupal.org/project/taxonomy_manager 
    http://drupal.org/project/term_node_count 
    http://drupal.org/project/terms_of_use 
    http://drupal.org/project/token (use 6.x-1.16)
    http://drupal.org/project/userprotect 
    http://drupal.org/project/user_register_notify 
    http://drupal.org/project/views (use 6.x-2.13)
    http://drupal.org/project/views_bonus 
    http://drupal.org/project/views_bulk_operations 
    http://drupal.org/project/views_customfield 
    http://drupal.org/project/views_data_export 
    http://drupal.org/project/views_dynamic_fields 
    http://drupal.org/project/views_export_xls 
    http://drupal.org/project/views_or 
    http://drupal.org/project/views_random_seed 
    http://drupal.org/project/views_send 
    http://drupal.org/project/views_tablesorter 
    http://drupal.org/project/views_tree 
    http://drupal.org/project/webform 
    http://drupal.org/project/wysiwyg

You should be able to use the most recent recommended 6.x versions of these modules with a few exceptions:

Token version 6.x-1.18 doesn't work with auto_nodetitle when the adminitrator is creating a new user.  The user first and last name do not get set correctly at the title of a user's content profile. 6.x-1.16 works fine.
Community Weaver 2.0 currently originally used a development version of Mutual Credit that was available after 6.x-2.2 was released.  We're now on 6.x-2.5.  BTW, we couldn't have done this project without Matthew Slater.  He's been a big help, and very responsive.

Views 6.x-2.16 caused some problems with custom fields.  2.15 may work, but we haven't extensively tested it.  We know 2.13 works.

The last release of views_send does not work with the newest version of views_bulk_operations.  A patch is supposedly available here: https://drupal.org/node/1200584 but we have not yet tested it.  The only release available now, a dev release, may or may not contain that patch.

### 3. Install Supporting Code Libraries

In [Drupal_Home]/sites/all/libraries you'll need the following related libraries:

    http://download.cksource.com/CKEditor/CKEditor/CKEditor%203.6.2/ckeditor_3.6.2.zip
    http://code.google.com/p/jquery-ui/downloads/detail?name=jquery.ui-1.6.zip&can=2&q=1.6
    http://tablesorter.com/__jquery.tablesorter.zip

### 4. Install the Required Theme

In addition you'll need the following themes:

    http://drupal.org/project/fusion
    http://drupal.org/project/acquia_marina

Both of these should be put in [Drupal_Home]/sites/all/themes.

### 5. Install Availability Check Grid module

Download the module from GitHub here: https://github.com/GeekGene/avail_cck_field/zipball/master
Unzip the file downloaded file.  Rename the directory to avail_cck_field and copy it to [Drupal_Home]/sites/all/modules/

### 6. Install Time Banks module

Download the module from GitHub here: https://github.com/GeekGene/GeekGene-time_banks/zipball/master

Unzip the file downloaded.  The time_banks directory should be installed in [Drupal_Home]/sites/all/modules/

### 7. Install Community Weaver 2.0

Download the whole Community Weaver package from here: https://github.com/GeekGene/Community-Weaver/zipball/master

Files that should included in download:

    CHANGELOG.txt    log of changes
    COPYRIGHT.txt      copyright statement, references GNU GPL 2.0
    LICENSE.txt           The GNU GPL 2.0 license agreement
    README                to be read
    tbtempl.sql.bz2       database dump

Uncompress the database file.  From the command line:

    tar xvf tbtempl.sql.bz2

Import the resulting .sql file into mysql:

    mysql -uroot -p   (enter your mysql root password when prompted)

   (mysql prompt) mysql>  create database drupal622_template;

   (mysql prompt) mysql> exit

   mysql -uroot -p < tbtempl.sql

The database name in this file is drupal622_template.  You can change that to whatever you like on the third line of the sql file using a text editor.  That's the only place it's used.  You'll need to set the database user and password yourself, and add those to your settings.php file. 

    mysql -uroot -p drupal622_template;

    (mysql prompt) mysql>  GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, LOCK TABLES, CREATE TEMPORARY TABLES ON drupal622_template.* TO username@localhost IDENTIFIED BY 'password';

    (mysql prompt) mysql> flush privileges;

### 8. Configure Various Community Weaver and Drupal System Components

In settings.php on the line that starts with $db_url change the settings to those you just used for database name (if you changed it), username, and password.  Thus:

     $db_url= 'mysqli://username:password@localhost/drupal622_template';

Resave the file and make sure only your user and group have read access with something like this:

     chmod 440 settings.php


In [Drupal_Home]/sites/all/themes/acquia_marina create a symbolic link to ../../modules/time_banks/theme/mc_3rdparty_formspecial.tpl.php

    ln -s ../../modules/time_banks/theme/mc_3rdparty_formspecial.tpl.php

In [Drupal_Home]/sites/all/themes/acquia_marina/css create a symbolic link to ../../../modules/time_banks/theme/local.css (If acquia_marina comes with it's own local.css, delete it.)

   ln -s ../../../modules/time_banks/theme/local.css

We keep both of these files in the time_banks directory to make revision control a little easier.  And, if you blow them away when upgrading acquia_marina you've only lost symlinks and not entire files.  You won't need actionhub-override.css and store.css.  They're for some other related sites that are beyond the scope of setting up a single timebank.

### 9. Configure Apache Settings

You'll need to tell your webserver about this drupal installation.  Assuming apache is your webserver and it's installed on your server at /etc/apache, you'll need to edit your existing vhosts file or add a vhosts file just for this website.  Add something like the following to the end of your vhosts file:

```
    <VirtualHost *:80>
        ServerName [YOURSITE]
        ServerAlias *.[YOURSITE]
        DocumentRoot /[Drupal_Home]
        <Directory "/[Drupal_Home]">
            Order allow,deny
            Allow from all
            AllowOverride All
            Options FollowSymLinks
        </Directory>
    </VirtualHost>
```

if /etc/apache/vhosts is a directory, create a new text file with a filename of [YOURSITE] and add the previous text.  Rather than a vhosts file or directory, you have have a httpd.conf file.  The same text would go at the end of it.  You'll need to restart apache before these settings are used.

    sv restart apache

### 10. Configure Final Settings in Drupal

This installation comes only with the administrative user (uid=1). So now that your site is up and running, login with username "admin" and  password "password".  

Click the MY ACCOUNT tab and then click [ Edit User Account ] in the left sidebar.  After changing username, password, address, click save at the bottom of the page.

We've provided a copy of the database exactly as we use it on our server.  Thus, there are a few more things you'll need to set up inside Drupal.

Flush all caches.  From the admin bar at the top of the page, click the icon next to Content management, and then click Flush All Caches

Change file path.  Browse to http://[YOURSITE]/admin/settings/file-system. Change to sites/[YOURSITE]/files

Turn off the rule "add to coordinators list" in http://[YOURSITE]/admin/rules/rules/rules_add_coordinator_to_list/edit.  This rule calls a function in time_banks.module that uses custom email list handling functionality outside the scope of a single timebank.

Click "rule settings" and uncheck "This rule is active and should be evaluated when the associated event occurs.", click save.

Delete the action "time_banks_manage_lists" on http://[YOURSITE]/admin/settings/actions.  This is more email list management.


Set your site name and site-wide email on http://[YOURSITE]/admin/settings/site-information. If using drush, they are variables site_name and site_mail

Set site-wide contact email recipient on http://[YOURSITE]/admin/build/contact/edit/1

Set user register notify email on http://[YOURSITE]/admin/settings/register_notify. Is drupal variable user_register_notify_mailto

Set time_banks_coord_email to be the same as site_mail.  This is used as the from address for Guardian Angel notifications.  If not using drush, you can use the devel module to change this variable in http://[YOURSITE]/devel/variable.  This is also in the admin bar.

Set drupal variable views_send_from_mail_broadcast_email:page_1 to your site_mail. 

Set drupal variable views_send_from_name_broadcast_email:page_1 to your site_name  Both of these can also be edited in the variable editor.

We hide both of these fields with css on the Send Broadcast Email Page (the css is in the footer of the view).

The header of the marketplace view http://[YOURSITE]/admin/build/views/edit/marketplace references three icons not included.  Set these to whatever you like or remove the html.

Edit the footer block visible on all pages at http://[YOURSITE]/admin/build/block/configure/block/5?destination=welcome which references a TimeBanks USA logo.  Set to whatever you like or remove the html.
Enjoy Your New Timebank

