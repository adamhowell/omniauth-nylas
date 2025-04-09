# Omniauth::Nylas

[![Gem Version](http://img.shields.io/gem/v/omniauth-nylas.svg)][gem]
[![Build Status](https://travis-ci.org/kwbock/omniauth-nylas.svg?branch=master)][travis]

[gem]: https://rubygems.org/gems/omniauth-nylas
[travis]: http://travis-ci.org/kwbock/omniauth-nylas

[OmniAuth](https://github.com/intridea/omniauth) Strategy for [nylas.com](nylas.com). Compatible with OmniAuth 2.0.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'omniauth-nylas'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install omniauth-nylas

## Usage

### Sinatra

```ruby
require "sinatra"
require "omniauth"
require "omniauth-nylas"

# For OmniAuth 2.0, protect against CSRF
OmniAuth.config.allowed_request_methods = [:post]

class MyApplication < Sinatra::Base
  use Rack::Session::Cookie, secret: ENV['SESSION_SECRET']
  use OmniAuth::Builder do
    provider :nylas, ENV['NYLAS_CLIENT_ID'], ENV['NYLAS_CLIENT_SECRET']
  end
end
```

### Rails
In `config/initializers/omniauth.rb`
```ruby
# For OmniAuth 2.0, protect against CSRF
OmniAuth.config.allowed_request_methods = [:post]
# If you need to test your app in development and don't want to post the form every time
# OmniAuth.config.allowed_request_methods = [:post, :get] if Rails.env.development?

Rails.application.config.middleware.use OmniAuth::Builder do
  provider :nylas, ENV["NYLAS_CLIENT_ID"], ENV["NYLAS_CLIENT_SECRET"]
end
```

## Development

After checking out the repo, run `bundle install` to install dependencies. Then, run `rake spec` to run the tests.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/kwbock/omniauth-nylas.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
