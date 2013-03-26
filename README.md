# Description

Installs packages via attributes or data bag metadata.

# Requirements

## Chef

No specific version requirements. Tested on 11.4.0.

## Platform

The following platforms have been tested with this cookbook, meaning that the
recipes run on these platforms without error:

* arch
* ubuntu

# Installation

With librarian-chef, add:
    cookbook 'package-driver',
      :github => 'markhibberd/package-driver'

# Usage

Include `recipe[package-driver]` in your run_list and populate the
`node['packages']` attribute.
# Recipes

## default

Install a list of packages, specified by node['packages'].

To use this simply create an item in the packages data bag. For example,
`data_bags/packages/all.json`:

    {
      "id": "all",
       packages: [
           "nodejs",
           "ghc"
       ]
    }

Then specify the item name.

node['packages'] = [ 'all' ]

# Attributes

## `data_bag`

Specify the data bag to pull package information from.

## `items`

Specify the _name_ of the attribute to use to populate the package lists.

For example if you wanted to define you packages with 'install-me' you would:

node['package-driver']['items'] = 'install-me'
node['install-me'] = [ 'postgresql', 'ghc' ]

# Resources and Providers

None yet.

# Development And Issues

* [https://github.com/markhibberd/package-driver](https://github.com/markhibberd/package-driver)

The implementation is currently pretty sparse. Plan to add more in the near future. Any suggestions, issues or patches are very welcome.

# License and Author

Author:: Mark Hibberd <mark@hibberd.id.au>

Copyright:: 2013, Mark Hibberd

All code is copyright 2013 Mark Hibberd <mark@hibberd.id.au>

All code is licensed under a 3-point BSD style license.

See LICENSE or https://github.com/markhibberd/package-driver/blob/master/LICENSE.


## Related

* [user](http://community.opscode.com/cookbooks/user) - Creates users from data bags using a similar process.
* [dpkg_packages](http://community.opscode.com/cookbooks/dpkg_packages) - Installs debian packages using, among other things, data bags for specifying details.
