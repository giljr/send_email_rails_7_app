
# Project Send Email via Rails 7

### This is a working code 👌️

How to send email in Rails 7?

In Rails 7, you can use the Action Mailer framework to send emails. Action Mailer provides a set of methods and conventions for sending email messages from your Rails application. Here's an example of how to send an email using Action Mailer in Rails 7:

Generate a new mailer:

Copy code
rails generate mailer MyMailer
This command will generate a new mailer file (my_mailer.rb) in the app/mailers directory, along with a corresponding view directory (app/views/my_mailer).

1) Open the generated mailer file (```app/mailers/my_mailer.rb```) and define a method for the email you want to send. For example:

```ruby
class MyMailer < ApplicationMailer
  def welcome_email(user)
    @user = user
    mail(to: @user.email, subject: 'Welcome to My App')
  end
end
```
In this example, the welcome_email method takes a user object as a parameter. It sets the ```@user``` instance variable, which can be used in the corresponding view.

2) Create a view file for the email (```app/views/my_mailer/welcome_email.html.erb``` or ```app/views/my_mailer/welcome_email.text.erb```). You can use either HTML or plain text format, depending on your needs.

3) To send the email, you can call the mailer method from a controller or any other part of your application. For example:

```ruby
MyMailer.welcome_email(user).deliver_now
```

Replace ```user``` with the actual user object you want to send the email to.

That's it! This is a basic example of sending an email in Rails 7 using Action Mailer. You can customize the email content, add attachments, use mailer layouts, and configure email delivery settings according to your requirements. Be sure to check the Rails documentation for more information on advanced email features and options.

### SMTP Configuration to send email Rails:

Go To: ```config/environments/development.rb```

  ```ruby
  config.action_mailer.perform_deliveries = true
  config.action_mailer.raise_delivery_errors = true
  config.action_mailer.default_options = {from: '<your_email@gmail.com>'}
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
  address:              'smtp.gmail.com',
  port:                 587,
  domain:               'JAYTHREE',
  user_name:            '<your_email@gmail.com>',
  password:             GOTO: https://myaccount.google.com/apppasswords,
  authentication:       'plain',
  enable_starttls_auto: true          }
  ```

## Acknowledgements

 - [Rails Mailer Tutorial](https://medium.com/@ericschwartz7/rails-mailer-tutorial-82700f6737d9) by Eric Schwartz

