# Htmlcompressor

## Put your html on a diet

Htmlcompressor provides tools to minify html code.
It includes
- HtmlCompressor::Compressor class which is a raw port of [google's htmlcompressor](http://code.google.com/p/htmlcompressor/)
- HtmlCompressor::Rack a rack middleware to compress html pages on the fly

Please note that Htmlcompressor is still in alpha version and need some additional love.

## Usage

Using the compressor class is straightforward:

```ruby
  compressor = HtmlCompressor.Compressor.new
  compressor.compile('<html><body><div id="compress_me"></div></body></html>')
```

The compressor ships with some default option that may be overwritten passing the options hash to the constructor:

```ruby
  option = {
    :enabled => true
    :remove_multi_spaces => true,
    :remove_comments => true,
    :remove_intertag_spaces => true,
    :remove_quotes => true,
    :compress_css => false,
    :compress_javascript => false,
    :simple_doctype => false,
    :remove_script_attributes => true,
    :remove_style_attributes => true,
    :remove_link_attributes => true,
    :remove_form_attributes => false,
    :remove_input_attributes => true,
    :remove_javascript_protocol => true,
    :remove_http_protocol => true,
    :remove_https_protocol => false,
    :preserve_line_breaks => false,
    :simple_boolean_attributes => true
  }
```

Using rack middleware is as easy as:

```ruby
  config.middleware.use HtmlCompressor::Rack
```

It is not yet possible to override default options when using the rack middleware.

Rails 2.3 users may need to add
```ruby
  require 'htmlcompressor'
```

## Statistics

As of now the statistic framework hasn't been ported. Refer to original [htmlcompressor documentation](http://code.google.com/p/htmlcompressor/) for statistics on minified pages.

## License

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
