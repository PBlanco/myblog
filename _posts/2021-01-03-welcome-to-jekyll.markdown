---
layout: post
title:  "Cheap blogging with Jekyll"
date:   2021-01-03 17:57:37 -0500
categories: life 
---
tl;dr How to host your blog using Jekyll and AWS Amplify

The first thought you might have when you decide to make a blog is "wow I have a big ego". Your second thought might be "what do I have to write about".

Well, if your answer is nothing then you can write about **how you made a cheap blog**. That is what I've done. This blog post is about hosting your own cheap blog.

### Prerequisites
1. Github and AWS account
3. Some familiarity with coding and your [terminal](https://en.wikipedia.org/wiki/Terminal_%28macOS%29)
4. [Homebrew](https://brew.sh) Package Manager

### Cost of blogging by platform
At the time of writing (Jan 2021) here are the prices I found online to use your own custom domain (i.e. blancotech.com). Ingnoring the price to maintain the domain (I use go daddy and it's around $20/year)
|Site| Cost |
|--|--|
| Ghost | $348/year |
| Blogger | $144/year |
| Squarespace | $144/year |
| Wordpress | $48/year |
| Medium | $0/year |
| Github | $0/year |
| Jekyll + AWS Amplify | $0/year |

To be honest, I did this price analysis after and didn't know Medium was free. Also, I didn't think to use GitHub. So, do what you like 🤷‍♂️.

### Using Jekyll

[Jekyll](https://jekyllrb.com) is a static website and blog framework. It's easy to get up and running. You can choose [custom templates](https://jekyllthemes.io/free) for your blog and easy create new posts using [markdown](https://en.wikipedia.org/wiki/Markdown) syntax. 

#### Setup
I tried to follow the instructions on their site https://jekyllrb.com and input into my terminal

    gem install bundler jekyll

 but it immediately errored. Ended up 

    $ gem install bundler jekyll
    Fetching bundler-2.2.4.gem
    ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.

Through stack overflow I determined it was because I was using an older version of ruby that was native on my Mac OS. To confirm this I checked what my system was using

    $ which ruby
    /usr/bin/ruby
    $ which gem
    /usr/bin/gem


So, I decided to install the latest version of Ruby using Homebrew 

    brew install ruby

Next, I needed to tell my environment to look to the ruby installed by homebrew. To do this I added the path to my .zshrc using
```$ echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/2.7.0/bin:$PATH"' >> ~/.zshrc```

Then refreshed my terminal `$ source ~/.zshrc`

After
$ which ruby
/usr/local/opt/ruby/bin/ruby
and 
$ which gem
/usr/local/opt/ruby/bin/gem

Then running `$ gem install bundler jekyll` worked!

After I went to the directory I wanted to create my project in. Then ran `jekyll new personalsite`

once there I was able to run `jekyll serve` to launch my site and could go to my browser to view it under `localhost:4000`.

### How to get it online

So the blog was created! But how do I get it online? To do this, I followed the tutorial [here](https://medium.com/@jameshamann/deploy-your-jekyll-site-using-aws-amplify-with-only-a-few-clicks-8f3dd8f26112) on using AWS Amplify.

The one caviate I have is I ndeded to get my repository into github. To do this, I went to my github and created a new repositoy with nothing add to it (no git ignore etc). Then, I went back to my terminal and ran `git init`. Then, `git add .` to add files. Then `git commit -m "My first commit"` Finally added 
`$ git remote add origin git@github.com:PBlanco/personalsite.git` so that I could push my commited change to github. 

To push to github, I copied the link from my newly created repositoy and added it as a remote repo `$ git remote add origin git@github.com:PBlanco/personalsite.git` Then pushed the code `$ git push -u origin master`.

After, I followed the linked steps above.