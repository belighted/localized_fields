# Mongoid::Textile [![Build Status](https://secure.travis-ci.org/tiagogodinho/mongoid-textile.png)](http://travis-ci.org/tiagogodinho/mongoid-textile) [![Build Status](https://gemnasium.com/tiagogodinho/mongoid-textile.png?travis)](http://gemnasium.com/tiagogodinho/mongoid-textile)

Helps you to create forms with localized fields using Mongoid.

## Installation

Add this line to your application's Gemfile:

    gem 'localized_fields'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install localized_fields

## Usage

Localized Fields uses

`app/models/post.rb`

```ruby
class Post
  include Mongoid::Document

  field :title, localize: true
end
```
`app/controllers/posts_controller.rb`

```ruby
def new
  @post = Post.new
end
```

### Automatic

`app/view/posts/_form.html.erb`

```erb
<%= form_for @post do |f| %>
  <%= f.localized_fields do |localized_fields| %>
    <%= localized_fields.label :title %>
    <%= localized_fields.text_field :title %>
  <% end %>
<% end %>
```
### Detailed

`app/view/posts/_form.html.erb`

```erb
<%= form_for @post do |f| %>
  <%= f.localized_fields :title do |localized_fields| %>
    <%= localized_fields.label :en %>
    <%= localized_fields.text_field :en %>

    <%= localized_fields.label :pt %>
    <%= localized_fields.text_field :pt %>
  <% end %>
<% end %>
```

## Dependencies

- rails >= 3.1
- mongoid >= 2.4

## Compatibility

Localized Fiedls is tested against Ruby 1.8.7, 1.9.2, 1.9.3, REE and Rubinius.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

MIT License. Copyright 2012 Tiago Rafael Godinho
