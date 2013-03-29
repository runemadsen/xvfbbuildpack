# Sinatra-Heroku Template

This small application shows you how to use @ddollar's heroku multi-buildpack to run Xvfb on Heroku.

to use it do this:

```
$ heroku create someapp --buildpack https://github.com/ddollar/heroku-buildpack-multi.git
$ heroku config:add LD_LIBRARY_PATH=/app/lib
```