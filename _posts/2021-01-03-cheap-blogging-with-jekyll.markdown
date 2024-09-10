---
layout: post
title:  "Cheap blogging with Jekyll"
date:   2021-01-03 17:57:37 -0500
---

**tl;dr How to host your blog using Jekyll and AWS Amplify**

The first thought you might have when you decide to make a blog is "wow I have a big ego". Your second thought might be "what do I have to write about".

Well, if your answer is nothing then you can write about **how you made a cheap blog**. That is what I've done. This blog post is about hosting your own cheap blog.

### 🎯 Prerequisites
1. Github and AWS account
3. Some familiarity with coding and your [terminal](https://en.wikipedia.org/wiki/Terminal_%28macOS%29)
4. [Homebrew](https://brew.sh) Package Manager

### 💸 Cost of blogging by platform
At the time of writing (Jan 2021) here are the prices I found online to use your own custom domain (i.e. blancotech.com). Ignoring the price to maintain the domain (I use go daddy and it's around $20/year)

| Site | Cost |
|-----|-----|
| Ghost | $348/year |
| Blogger | $144/year |
| Squarespace | $144/year |
| Wordpress | $48/year |
| Medium | $0/year |
| Github | $0/year |
| 🌟 **Jekyll + AWS Amplify** | **$0/year** |

To be honest, I did this price analysis after and didn't know Medium was free. Also, I didn't think to use GitHub. So, do what you like 🤷‍♂️.

### ⚙️ Setting up Jekyll

[Jekyll](https://jekyllrb.com) is a static website and blog framework. It's easy to get up and running. You can choose [custom templates](https://jekyllthemes.io/free) for your blog and easily create new posts using [markdown](https://en.wikipedia.org/wiki/Markdown) syntax. 

I'm using a MacBook on Mac OS Big Sur v11.1. I first tried to follow the instructions on Jekyll's site https://jekyllrb.com and input them into my terminal

    $ gem install bundler jekyll

 but this immediately errored

    $ gem install bundler jekyll
    Fetching bundler-2.2.4.gem
    ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.

I determined it was because I was using the ruby that is native on my Mac OS. To confirm this I checked what my system was using

    $ which ruby
    /usr/bin/ruby
    $ which gem
    /usr/bin/gem


To install the latest version of Ruby I used [Homebrew](https://brew.sh) 

    $ brew install ruby

Next, I told my shell environment to use the ruby installed by homebrew. By adding the path to my shell file `~/.zshrc`. 

    $ echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/2.7.0/bin:$PATH"' >> ~/.zshrc

Then I refreshed my terminal with the file using `$ source ~/.zshrc`. Alternatively, you can open a new terminal window and this will do the same thing.

> ⚠️ If you're not using [ohMyZsh](https://ohmyz.sh) then replace the `~/.zshrc` in the above command with `~/.bash_profile`. 

To confirm that you're using the brew installed ruby run

    $ which ruby
    /usr/local/opt/ruby/bin/ruby
    $ which gem
    /usr/local/opt/ruby/bin/gem

Then running `$ gem install bundler jekyll` worked 🎉!

### 🛠 Create your project

To create your project go to the directory you want to create it in. Next, run `jekyll new myblog`. You can replace `myblog` with whatever name you'd like to give it.

Run `jekyll serve` to launch your site and view it in your browser at the URL `localhost:4000`.

### 🌐 How to get your code into a repository
In order to get your site online, you'll need to put your code into a repository. For this, I used [GitHub](http://github.com/). 

1. Go to your GitHub and create a new repository with nothing added to it (no git ignore, etc). 
2. Setup the repository by running `git init` in your project's directory in your terminal
3. Add the files you will commit by running `git add .` in your terminal
4. Commit the changed files by running`git commit -m "My first commit"` in your terminal
5. Tell your repository where to push the code by copying the repositories link from GitHub then running `$ git remote add origin <your_link>` in your terminal. Your link will look something like `git@github.com:YourUserName/yourlink.git`
6. Finally, push the code by running `git push -u origin master`

### 🌐 How to get your site online

So the blog was created! To host it online for the world to access it use AWS Amplify and follow the tutorial here: [Deploy your Jekyll Site using AWS Amplify — with only a few clicks](https://medium.com/@jameshamann/deploy-your-jekyll-site-using-aws-amplify-with-only-a-few-clicks-8f3dd8f26112).

You now have a blog using Jekyll hosted on AWS Amplify 🍻.
