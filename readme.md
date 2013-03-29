# Sinatra-Heroku Template

This small application shows you how to use @ddollar's heroku multi-buildpack to run Xvfb on Heroku.

to use it do this:

```
$ heroku create --buildpack https://github.com/ddollar/heroku-buildpack-multi.git
$ heroku config:add LD_LIBRARY_PATH=/app/lib
```


Then you can run `heroku run bash` and do the following:

```
$ irb
$ > require 'bundler'
$ > Bundler.require
$ > sketch = P5::Sketch.new("/app/sketch", "/tmp/testbuild")
$ > sketch.run
$ > AWS::S3::Base.establish_connection!(:access_key_id => 'key', :secret_access_key => 'secret')
$ > AWS::S3::S3Object.store("grab.png", open("/tmp/grab.png"), 'mybucket')
```