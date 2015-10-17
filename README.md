# Ravelry

_You are reading documentation for version: 0.0.2_

[ ![Codeship Status for ArtCraftCode/ravelry](https://codeship.com/projects/fc6710e0-5719-0133-36cc-5ebc52a48109/status?branch=0.0.2)](https://codeship.com/projects/109462)

This gem is actively being developed. Be sure to check the branch for the version you're using as breaking changes can (and will!) be introduced.

To see what I am working on next, visit the project's [Trello board](https://trello.com/b/o8gs4cWI/ravelry).

The Ruby gem for accessing the Ravelry API painlessly, easily, and awesomely.

Ravelry API documentation is currently available [here](http://www.ravelry.com/api).

## API coverage

* `Patterns#show` (`GET`)

# Installation

Welcome to a magical land where gems rule the world. To install, type:

```
gem install ravelry
```

Hooray! You now have a gem.

Add to your `Gemfile`:

gem "ravelry", "~> 0.0.2"

**I highly recommend pinning your version** because the gem is in active development and I _promise_ I will break shit.

Run `bundle install` and proceed as usual.

## API keys

API keys must be configured in the gem setup. You can do this anywhere in your application before you make API calls using the gem.

```ruby
Ravelry.configure do |config|
  config.access_key = ''
  config.secret_key = ''
  config.personal_key = ''
end
```

* `config.access_key` - your Ravelry access key
* `config.secret_key` - your Ravelry secret key
* `config.personal_key` - wait for it! Your Ravelry personal key; primarily used for OAuth (not yet implemented in the gem)

Getting these keys requires a (free) Ravelry account and that you agree to the terms of use for the API.

# Usage

Full documentation for this gem is available [here](http://www.rubydoc.info/gems/ravelry/0.0.2).

# API quirks

## Accessing pattern ids (for `Ravelry::Patterns`)

To use the `Patterns#show` endpoint, you need the pattern id from Ravelry. You can use the pattern search API to search for the pattern name and get this information, but that is not yet implemented in the gem.

In the meantime, navigate to a pattern page in Ravelry and open up the JavaScript console. Type this in:

```javascript
$$('.difficulty').first().id
```

You should see something like this: ```"pattern_419443_difficulty_score"```.

```419443``` is your pattern id.

# Conventions

This gem makes use of several conventions that are worth noting on a global scale.

## Method names ending with `_count` return integers.

Example:

```ruby
pattern.comments_count
# => 4
```

## Method names ending with `_float`, `_integer`, etc return that object type.

Float to Integer conversions are done using round(0).

Example:

```ruby
pattern.difficulty_average_float
# => 4.666666667

pattern.difficulty_average_integer
# => 5
```

# Contributing

Hey! You want to contribute? That is super, super awesome. Visit the project's [Trello board](https://trello.com/b/o8gs4cWI/ravelry) to see what's coming up next or what is already in progress.

Send me a pull request! Note that your pull request will not be accepted if you don't write tests **and documentation** for your code (the test part kind of goes without saying, but I wanted to make sure that you knew about it and the documentation).

To run specs locally, simply `bundle` and then run `rpsec`.

Documentation is generated by YARD and is producted using inline comments. Comments use Markdown syntax. You can run `yard server` to get a live server of documentation while you're working :)
