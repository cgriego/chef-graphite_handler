Description
===========

Report [Chef](http://www.opscode.com/chef) stats to [Graphite](http://graphite.wikidot.com/) using the [chef-handler-graphite gem](https://github.com/imeyer/chef-handler-graphite).

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
