# Moodle Update Script
To automate __our environment__ we wrote this bash script. It may won't work in your environment, but maybe you get some ideas for your own script.


## Setup
1. Clone this repository.
1. Make the script executable (if not cloned): `chmod +x moodle-update`
1. Go to your web directory: `cd /var/www`
1. Rename the moodle directory to: `moodle_x.y` like `moodle_4.01`
1. Create a link to this directory with the absolute path: `ln -s /var/www/moodle_4.01 moodle`
1. Tell your web server to serve `/var/www/moodle`.


### Config
The script creates a `settings.conf` file for a standard Debian/Ubuntu Linux.

**But don't worry**: If something is not working, the tests will fail before any changes would be performed. Adapt the `settings.conf` to your needs and re-run the script.


## Usage options
- Without any parameter: `./moodle-update`
- With new version: `./moodle-update 3.9`
- With new version + explicit download file: `./moodle-update 3.9 https://example.com/moodle-3.9.21.zip`


### Important information for Moodle 4
For some reason the latest zip file name scheme has changed:

- `4.1` is called `401` (instead of `41`)
- `4.2` is called `402` (instead of `42`)
- _(future versions may be affected too)_

You need to enter `4.01` or `4.02` as version number to use the script for these versions!


## Plugins
- Within a minor release (3.9.19 -> 3.9.21) you should be fine to use the `copy all` option.

- If you're updating from one minor release to another (3.9 -> 3.11) or upgrading from one major release to another (3.11 -> 4.0) some plugins should not be copied over. Please use a test server to figure out which of your installed plugins cause problems.
