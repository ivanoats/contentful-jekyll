*Work in progress - do not try this yet, incomplete*

# Creating Static Sites for clients with Contentful, Aerobatic, and Jekyll

Many small agencies are facing a challenge:  How to create a high-performing web site, while at the same time, let the client edit blog posts and pages.  Fortunately, a combination of services and open-source tools has made this possible now. [Contentful](https://www.contentful.com) provides the web site where content is edited. [Jekyll](https://jekyllrb.com) provides the the code that turns content into webpages. And [Aerobatic](https://www.aerobatic.com) provides the high-performance hosting system. Research has shown that speedy sites translate into more engaged visitors and higher search engine rankings.

What does this all replace? The decade old solution to this has been WordPress, or another PHP based content management system (CMS). But in addition to the code in WordPress showing its age, it may not be the right solution for everyone. The admin interface for WordPress is too complex for many clients. It is powerful, but also gives people "enough rope to hang themselves on". And while WordPress has made progress on core security, the many plugins and their required updates take a lot of time, and introduce potential security risks. To create a WordPress theme, the front-end designer must leave the comfortable world of HTML, CSS, and JavaScript, and also learn some PHP.

## What is a Static Site, and why use it?

A static site is a website that has no code running on the server. It does not mean the web site does not change. Static sites typically take less than 5 minutes to build, and can be updated all day long if necessary. Browser-based JavaScript can talk to web services via application programming interfaces (APIs) and provide a dynamic, customized experience to the site visitor.

Static site generators have recently seen a lot of growth, and for good reason. Static sites can be optimized for high performance, because there is no code to run on the server to slow things down. Static sites can be distributed globally on a content distribution network (CDN) so that site visitors can get the content more quickly.

And most importantly, static sites are simple. They are easier to debug and optimize, because there are fewer "moving parts". For example, on Aerobatic, getting a site online and globally distributed is three steps:

## Getting started with Aerobatic

[Aerobatic](https://www.aerobatic.com) offers a hosting service specifically tailored to static website publishing, that is simple and powerful.

1. Install NodeJS. If you haven't already, see the [downloads page](https://nodejs.org/en/download/).

2. Open a command line window and install Aerobatic:
```
npm -g install aerobatic cli
```
3. Create an html page. In this example we'll use something ridiculously simple to prove the point.
```html
 echo "<h1>Hello World</h1>" >> index.html
```
4. Login to Aerobatic and copy the index.html page up to the service:
```
aero login && aero deploy
```

Granted, that was, of course, the bare minimum. A more robust static site can be built with a tool called [Jekyll](http://jekyllrb.com). Jekyll was released in May 2013. It is used by thousands, if not tens of thousands of sites. It has the most available themes, currently numbering around XXXX.

## Getting started with Jekyll

1. Install Ruby. Many of you will already have it installed. If not, see the [installation instructions](https://www.ruby-lang.org/en/documentation/installation/)
2. Install Jekyll:
```gem install jeykll```
3. Create your Jekyll site:
```jekyll new mysite```
(Replace mysite with whatever you want)

You can preview your new site with `jekyll serve`.

Adjust your `aerobatic.yml` file to push the `_site` directory.
```yaml
deploy:
   directory: _site
 ---
```

And re-publish your site with `aero deploy`

## Getting started with Contentful

- create a post content type with title and body
- get your space id
- get an API key

## Integrating Contentful and Jekyll

- edit the `Gemfile` to include jekyll-contentful-data-import
- create `_config-secret.yml` with contentful's spaceId and key
- run `jeyll contentful` (with secret config)
- check data files exist
- transform data files into blog posts with liquid magic

## Wrapping Up

Where to take it from here? It's up to you!

- Add advanced features with Aerobatic's [plugins](https://www.aerobatic.com/docs/plugins/) For example check out the [form-submit](https://www.aerobatic.com/docs/plugins/form-submit/) plugin to add a contact form to your site.
 - Add different content types with Contentful
- Optimize your site for speed with [WebpageTest](https://www.webpagetest.org)
- Set your site up for [Continuous Integration](https://www.aerobatic.com/docs/static-site-generators/#jekyll)
