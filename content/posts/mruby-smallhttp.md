---
title: "Revolutionize Your HTTP Requests with mruby-smallhttp"
date: 2017-04-04T15:21:41+01:00
---

Hi there,

I have updated your article for you. I hope you like it.

---

## Introducing Mruby-Smallhttp: A Simple HTTP-Client Library

While working on my [Telegram API library](https://github.com/nsheremet/mruby-tbot), I ran into a problem finding a good HTTP-client library that could handle `multipart/form-data` requests. I also found that some libraries required me to form the body of the requests myself, which was time-consuming and not very efficient.

I decided to solve this problem and wrote a library that is a small, less than 200 lines of code, HTTP-client library. While there are still some small issues that need fixing, I believe this library is a great start, and I am hoping for contributions from the community to make it even better.

So, let me introduce you to [Mruby-Smallhttp](https://github.com/nsheremet/mruby-smallhttp).

### Installing Mruby-Smallhttp

Installing Mruby-Smallhttp is a simple and straightforward process. Here are the steps to follow:

- Add the following line to your `build_config.rb` file:

```ruby
MRuby::Build.new do |conf|
  conf.gem :mgem => 'mruby-smallhttp'
end
```

And you're done! It's that simple.

### How to Use Mruby-Smallhttp

Using Mruby-Smallhttp is also very easy. Here are some examples of how to use it:

#### Making GET Requests

```ruby
# GET Request
HTTP.new("https://example.com/api/v1/users").get
#=> response
```

#### Making POST Requests

```ruby
data = { name: 'value' }
headers = {'Content-Type' => 'application/json'}

HTTP.new("https://example.com/api/v1/users").post(data, headers)
#=> response
```

#### Making PUT Requests

```ruby
http = HTTP.new("https://example.com/api/v1/users/1")
http.put(data, headers)
```

#### Making DELETE Requests

```ruby
http = HTTP.new("https://example.com/api/v1/users/1")
http.delete(data, headers)
#=> response
```

#### Making HEAD & OPTIONS Requests

```ruby
http = HTTP.new("https://example.com/api/v1/users/1")
http.request("HEAD", body, header)
#=> response
```

### Sending Files

If you need to send a file in your POST request, here's how to do it:

```ruby
body = { name: 'value', file: File.read('filename') }
header = { 'Content-Type' => 'multipart/form-data' }
http = HTTP.new("https://example.com/api/v1/users/1")
http.post(body, header)
#=> response
```

`Content-Type` supported: `application/json`, `application/x-www-form-urlencoded`, `multipart/form-data`.

### Conclusion

Mruby-Smallhttp is a simple, lightweight HTTP-client library that can handle different types of requests, including multipart/form-data requests. Although it's still a work in progress, I am confident that it will be a great addition to your toolbox. If you're interested in contributing to the project, please visit the [Mruby-Smallhttp Github page](https://github.com/nsheremet/mruby-smallhttp) to get started.

Thank you for reading!