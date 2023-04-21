---
title: "Parsing Hanami Controllers: Adventures in Creating API Documentation from RSpec Specs"
date: 2017-07-18T15:21:41+01:00
---

### Generating API Documentation with RSpec in Hanami Framework

A couple of days ago, I was searching for a library that would generate API documentation from RSpec specs. However, I encountered one significant problem – Hanami Framework. We use Hanami for several projects because it has a good structure and lacks ActionSupport, among other pros. Unfortunately, I couldn't find any library for Hanami, only for Rails/Sinatra.

So, my first step was to find a good and straightforward library that already has basic modules for creating HTML pages with documentation or creating docs in JSON/pdf files. After that, I would start making changes in the code, which is step two.

My coworker sent me a link to this library: [reqres_rspec](https://github.com/reqres-api/reqres_rspec) gem. This lib generates HTML/JSON/pdf files and can even download generated files to Amazon S3. It seemed to me that this library has more capabilities than I needed. I decided to start working with it, and if I encountered any problems, I would look for another solution.

To collect data, the library parses files of Rails controllers and finds their actions with comments above. Here is a snippet of the code:

```ruby
def get_action_comments(controller, action)
  # This line is only for Rails
  lines = File.readlines(File.join(ReqresRspec.root, 'app', 'controllers', "#{controller}_controller.rb"))

  # Some code here
rescue Errno::ENOENT
  ['not found']
end
```

The library collects data from parsing action files and the testing environment. Tests provide a lot of information about requests and responses from actions that are currently in testing. However, the way RSpec works with Hanami actions is much different from what we know in Rails. There are no real HTTP requests with headers, among other differences. The most significant problems arise with session and cookies.

Here's an example of a simple Hanami RSpec spec:

```ruby
require_relative '../../../app/controllers/api/books'

RSpec.describe BooksApi::Controllers::Api::Book do
  let(:action)    { described_class.new }
  let(:params)    { Hash[] }
  let(:response)  { action.call(params) }
  let(:data)      { JSON.parse(response.last[0]) }

  describe 'with valid params' do
    it 'should return all books' do
      expect(response[0]).to eql(200)
      expect(data).not_to be_nil
    end
  end
end

```

The example demonstrates that if you send a `rack.session` id as a Cookie in a real running app, it will retrieve the session from Redis. However, if you send a Cookie in your test, you will only receive a Cookie header without the session. I did not try to understand why this is happening, but I suspect it's because of Rack. Hanami uses Rack, and `rack.session` id in Cookies also uses Rack, which leads to this issue with collecting data from tests. Unfortunately, I couldn't get information about URL, path, host, and query parameters.

To overcome this issue, I created a special comment above the `call` method. You can use it like this:

```ruby
module BooksApi::Controllers::Api
  class Book
    include PublicApi::Action

    # @method GET
    # @path /api/books
    # @host booksapi.com
    def call(params)
      # Some books stuff
    end
  end
end
```

This solution is temporary, and in future updates, I plan to extract the information from the routes.rb file, which defines the application's routes.

Apart from this issue, all other parts of the reqres_rspec gem were used. The gem allowed me to add sections and titles for all of my specs, making it easier to organize and structure the generated documentation.

ruby
Copy code
require_relative '../../../app/controllers/api/books'

RSpec.describe BooksApi::Controllers::Api::Book do
  # some `let` declarations here

  describe 'with valid params', had_section: 'Books' do
    it 'should return all books', had_title: 'All' do
      # some `checks` here
    end
  end
end
In conclusion, I am grateful to the author of the reqres_rspec gem for creating such a useful tool. With its help, I was able to generate API documentation from my Hanami application, which was not possible using other available libraries. If you want to contribute to the reqres_rspec gem or have suggestions, you can find the link to the repository in the article.

Thank you for reading.