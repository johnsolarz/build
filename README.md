Eight Seven Central WordPress developement framework running on git submodules - old school but works for us.

Install
-------

1. Navigate to local project directory
2. [Download](https://github.com/johnsolarz/esc-wordpress/zipball/master) or `git clone git@github.com:johnsolarz/esc-wordpress.git`
3. Run `git submodule update --init --recursive`
4. Rock that shit

To update old submodules:
```
git submodule foreach 'git fetch origin --tags; git checkout master;
git pull' && git pull && git submodule update --init --recursive
```

Config to-dos
-------------

In wp-config.php add:

```
/* Limit WordPress post type revisions */
define('WP_POST_REVISIONS', 5);
```
```
/* Define WordPress.com API Key */
define('WPCOM_API_KEY','your_api_key');
```

Create custom php.ini:

- SSH into account and copy default php.ini file into home directory:
  `cp /usr/local/lib/php.ini ~/php.ini`
- tell wp htaccess where to look for the new php.ini file (change 'wp' to match directory):
  `echo "SuPHP_ConfigPath $HOME" >> ~/public_html/wp/.htaccess`

In php.ini add:

```
; Increase memory limit (may already be set by default)
memory_limit = 256M
```
```
; Increase file size limit (may already be set by default)
upload_max_filesize = 128M
post_max_size = 128M
max_execution_time = 300
```
```
; Increase input vars
max_input_vars = 3000
```

Author
------

John Solarz<br>
[Eight Seven Central](http://eightsevencentral.com)
