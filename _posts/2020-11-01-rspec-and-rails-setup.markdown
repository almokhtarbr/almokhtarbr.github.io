---
layout: post
title:  "Rspec and rails setup"
date:   2020-11-01 10:10:21 +0100
categories: rspec ruby rails
---

<!-- add this to gemfile -->

```ruby
group:development,:test do
  gem "rspec-rails"
  gem "factory_bot"
end

group:test do
  gem "faker"
  gem "capybara"
  gem "database_cleaner"
  gem "launchy"
  gem "selenium-webdriver"
  gem 'fuubar', require: false
  gem 'simplecov', require: false
  gem 'capybara'
  gem 'database_cleaner'
end

```

<!-- run -->

```
bundle install
rake db:create:all
```

<!-- add .rspec file  and insert this: -->

```

--format documentation
--format Fuubar
--color

```

<!-- inside spec_helper.rb insert this: -->

```ruby
    require 'simplecov'
    require 'faker'
    SimpleCov.start
```