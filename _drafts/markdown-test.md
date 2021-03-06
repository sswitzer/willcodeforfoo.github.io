---
layout: post
title: "Markdown Test"
---
The [latest builds](http://www.iterm2.com/#/section/downloads) of iTerm2 support an [API for displaying images in the terminal](http://www.iterm2.com/images.html#/section/home). It can display any Base64-encoded PNG or JPEG image inline or as a download. Guess what, Poltergeist can render the current page as a... Base64-encoded PNG or JPEG! Let's combine the two with this little snippet of Ruby in our `spec_helper.rb` file:

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

```ruby
def show_screenshot(width = 640)
  print "\033]1337;File=;inline=1;width=#{width}px:"
  print page.driver.render_base64
  print "\a\n"
end
```

Combine this with a call to [Pry](http://pryrepl.org/)'s `binding.pry` and now you can interact with your page and see the results of your [capybara](https://github.com/jnicklas/capybara) commands. Kind of like a web browser, but in your terminal!

![Screenshot](http://cl.ly/VOZW/Screen%20Shot%202014-05-07%20at%2011.13.10%20AM.png)
