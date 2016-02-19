# -*- mode: ruby -*-
# vi: set ft=ruby :

#Vagrant.configure("2") do |config|
#
#   config.vm.provision :puppet do |puppet|
#      puppet.manifests_path = "puppet/manifests"
#      puppet.manifest_file  = "init.pp"
#      puppet.facter = {
#         # Specifying the LANG environment variable this way is a work around.
#         # The work around can be removed when this issue is fixed https://github.com/mitchellh/vagrant/issues/2270
#         "hack=hack LANG=en_US.UTF-8 hack" => "hack"
#      }
#   end
#end

dir = File.dirname(File.expand_path(__FILE__))

require 'yaml'
require "#{dir}/puphpet/ruby/deep_merge.rb"

configValues = YAML.load_file("#{dir}/puphpet/config.yaml")

if File.file?("#{dir}/puphpet/config-custom.yaml")
  custom = YAML.load_file("#{dir}/puphpet/config-custom.yaml")
  configValues.deep_merge!(custom)
end

data = configValues['vagrantfile']

Vagrant.require_version '>= 1.6.0'

eval File.read("#{dir}/puphpet/vagrant/Vagrantfile-#{data['target']}")

