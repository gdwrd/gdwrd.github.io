---
title: "From POSTMAN to Rust: Introducing getsb-cli for Command-Line HTTP Requests"
date: 2017-04-18T15:21:41+01:00
---

### From POSTMAN to Rust: Introducing getsb-cli

Hi everyone, I'm excited to share my latest project with you all. Two weeks ago, I started learning Rust for better development experience, and as a part of my learning process, I decided to rewrite my `mruby-smallhttp` library in Rust.

During my Rust learning process, I discovered Cargo, which is similar to the bundler in the Ruby world. With Cargo, I was able to generate a template for my Rust project, including the `Cargo.toml` manifest file and the `lib.rs` file, which serves as the main file for a Rust library.

If you're interested in learning more about Rust, check out the [Rust-Lang](https://www.rust-lang.org/en-US/index.html) website and [The Rust Programming Language Book](https://doc.rust-lang.org/book/).

Once I had my Rust library set up, I decided to write a command-line tool for sending HTTP requests. Previously, I had been using POSTMAN, but I wasn't a fan of the Electron framework it used. I don't like Chrome at all, and using it to work with POSTMAN was too much for me. So, I decided to use my `knock` library to write a command-line tool in Rust.

I quickly wrote the tool, which I named `getsb`, and I had to add some code to my `knock` library. Currently, `getsb` is at version v0.1.0, and I'm planning to add more features to it soon. I would be grateful for any help in improving it.

To install `getsb`, follow these steps:

```shell
$ git clone https://github.com/nsheremet/getsb-cli.git
$ cd getsb-cli
$ cargo build --release
```

After that, move the binary file to the bin directory.

For Linux:

```shell
$ sudo mv target/release/getsb /usr/local/bin
```

For macOS:

```shell
$ sudo mv target/release/getsb /usr/local/bin/getsb
```

For Windows, create a folder for `getsb` and add it to your PATH environment variable.

To use `getsb`, run the following command:

```shell
$ getsb POST https://example.com/api/data -b "key=value" -h "Content-Type: application/x-www-form-urlencoded"
```

For more information on using `getsb`, check out the [README.md](https://github.com/nsheremet/getsb-cli/blob/master/README.md) file.

Overall, I really enjoyed working with Rust. It's an awesome language that allows for safe memory management and has many other great features.

If you're interested in learning Rust, I highly recommend checking out the [Rust Programming Language Book](https://doc.rust-lang.org/book/) and the [Awesome Rust](https://github.com/kud1ing/awesome-rust) repository.

Finally, here are links to my Rust projects:

- [knock](https://github.com/nsheremet/knock)
- [getsb-cli](https://github.com/nsheremet/getsb-cli)

Thank you for reading, and I hope this post has inspired you to start learning Rust!