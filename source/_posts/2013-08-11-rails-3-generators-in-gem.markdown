---
layout: post
title: "Rails 3 generators in gem"
date: 2013-08-11 18:02
comments: true
categories: 
---

<!--more-->
###This is the folders structure in a gem.

{% codeblock %}
lib
  - generators
    - gemname
      install_generator.rb
      - templates
        (template files)
        
{% endcodeblock %}

### Install Generator

{% codeblock %}

require 'rails/generators'

module ModuleName
  module Generators
    class InstallGenerator < Rails::Generators::NamedBase
      include Rails::Generators::Migration
      
      source_root File.expand_path("../templates", __FILE__)
      
      generators...
      
      def self.next_migration_number(path)
          @migration_number = current_migration_number(path) + 1
          ActiveRecord::Migration.next_migration_number(@migration_number)
      end
  
    end
   
  end
end

{% endcodeblock %}


### Generators...
{% codeblock %}
def generators
           
    generate("controller" , "nameOfController")
    
    copy_file "fileWantYouCopy.rb"   , "app/models/destiniAndNameToCopiedFile.rb"
    
    migration_template("modelOfMigrate.rb"  , "db/migrate/modelOfMigrateDestini.rb")
end
{% endcodeblock %}

### migration_template

You need add this include to use migration_template
{% codeblock %}
include Rails::Generators::Migration
{% endcodeblock %}

You need to implement next_migration_number
{% codeblock %}
def self.next_migration_number(path)
      @migration_number = current_migration_number(path) + 1
      ActiveRecord::Migration.next_migration_number(@migration_number)
end
{% endcodeblock %}