---
title: "Say Goodbye to Fat Models: Introducing Faat, the Ruby Gem That Will Transform Your Rails Code!"
date: 2023-04-21T15:21:41+01:00
---

Introduction:

Hello everyone, let me introduce you to my first open-source project called Faat! It's a Ruby gem that will help you slim down your fat model. In this article, I will provide more details about Faat, its features, and how it can be used.

What is Faat?

Faat is a Ruby gem that helps you separate the business logic from your Rails model by using a resource-oriented approach. With Faat, you can easily create resources and forms that will handle the CRUD operations on your model. This makes your code more modular, easier to maintain, and testable.

Installation:

The installation process of Faat is straightforward. All you need to do is add the following line to your application's Gemfile:

```ruby
gem 'faat'
```

Then execute:

```bash
$ bundle
```

Or install it yourself by running:

```bash
$ gem install faat
```

Usage:

Once you have installed Faat, you can start using it. Faat comes with two generators, faat:resources and faat:forms. These generators will create the necessary files for you to start using Faat.

To generate a resource for your model, run the following command:

```bash
rails generate faat:resources {model_name}
```

This command will create a folder called `resources` in your `app` directory, and a file called `{model_name}_resource.rb`.

To generate a form for your model, run the following command:

```bash
rails generate faat:forms {form_name} {attribute_name}:{attribute_type}
```

This command will create a folder called `forms` in your `app` directory, and a file called `{form_name}_form.rb`.

Once you have generated the necessary resources and forms, you can start using them in your controllers. Here's an example of how you can use them:

```ruby
@post_form = PostForm.new(post_form_params)
if @post_form.valid?
    @post_resource = PostResource.new(@post_form)
end
```

The above code will create a new `Post` model and a new `Author` model, and associate them with each other. This is all done in the `PostResource` class, which handles the business logic of creating new posts.

Features:

Faat comes with several features that make it a powerful tool for separating business logic from your Rails models. Here are some of its key features:

1. Resource-oriented approach: Faat uses a resource-oriented approach to handle the CRUD operations on your models. This means that you can create resources that handle the creation, updating, and deletion of your models.

2. Form objects: Faat also comes with form objects that allow you to handle the validation of your models. This means that you can have separate objects that handle the validation of your models, making it easier to test and maintain your code.

3. Modular code: Faat helps you separate your business logic from your models, making your code more modular and easier to maintain.

4. Testability: Faat makes it easier to test your code by providing you with separate objects that handle the validation and CRUD operations on your models.

TODO:

The next step for Faat is to add a spec/test auto-generator. This will make it even easier to test your code and ensure that it works as expected.

Contributing:

Faat is an open-source project, and we welcome contributions from anyone. If you find a bug or have an idea for a new feature, please feel free to submit a pull request or open an issue on our GitHub page.

Conclusion:

Faat is a powerful tool for separating business logic from your Rails models. It makes your code more modular, easier to maintain, and testable. If you
