# ActiveRecord::Rack

Provides database connection management for standalone ActiveRecord apps built on top of Rack.

[![Build Status](https://secure.travis-ci.org/ioquatix/activerecord-rack.svg)](http://travis-ci.org/ioquatix/activerecord-rack)
[![Code Climate](https://codeclimate.com/github/ioquatix/activerecord-rack.svg)](https://codeclimate.com/github/ioquatix/activerecord-rack)
[![Coverage Status](https://coveralls.io/repos/ioquatix/activerecord-rack/badge.svg)](https://coveralls.io/r/ioquatix/activerecord-rack)

## Motivation

Unfortunately, in ActiveRecord 5.0, the `class ConnectionManagement` [was removed](https://github.com/rails/rails/issues/26947). So, I've copied it from 4.2 and released it here with minor improvements.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'activerecord-rack'
```

## Usage

In your `config.ru`, before any middleware that would use the database, insert:

```ruby
# Middleware below this point may require database access:
use ActiveRecord::Rack::ConnectionManagement
```

### Testing

I removed the auto-detection of a test environment from the original middleware. I did this because I like predictable and simple logic. If you want to restore this behaviour, I suggest you write

```ruby
unless RACK_ENV == :test
	use ActiveRecord::Rack::ConnectionManagement
end
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## See Also

- [ActiveRecord::Migrations](https://github.com/ioquatix/activerecord-migrations)

## License

Released under the MIT license.

Copyright, 2016, by [Samuel G. D. Williams](http://www.codeotaku.com/samuel-williams).

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
