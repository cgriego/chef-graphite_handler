Description
===========

Report [Chef][1] stats to [Graphite][2] using the [chef-handler-graphite gem][3].

This cookbook uses the `chef_gem` resource added in Chef 0.10.10. If you are using an earlier version of Chef, then you can install the [chef_gem cookbook][4] which backports this functionality.

[1]: http://www.opscode.com/chef
[2]: http://graphite.wikidot.com/
[3]: https://github.com/imeyer/chef-handler-graphite
[4]: http://community.opscode.com/cookbooks/chef_gem

Attributes
==========

* `node['graphite_handler']['graphite_host']` - What host Graphite is running on, required.
* `node['graphite_handler']['graphite_port']` - What port Graphite is running on, required.
* `node['graphite_handler']['metric_key']` - The metrics key to use with Graphite, defaults to `"stats.#{node.chef_environment}.deployment.chef.#{node.name}"`.
* `node['graphite_handler']['version']` - Set the version of the chef-handler-graphite gem to install.

Any additional graphite_handler attributes will be passed directly into the GraphiteReporting class.

Usage
=====

Add `recipe[graphite_handler]` to your run list and set the required attributes.

``` ruby
run_list("recipe[graphite_handler]")
default_attributes("graphite_handler" => {
  "graphite_host" => "your-graphite-host",
  "graphite_port" => "your-graphite-port",
})
```
