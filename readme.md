# Heroku xvfb buildpack

This is a simple repo that demonstrates how to run (the right now very hacky) custom binary of Xvfb on Heroky. Thanks to @jallwine for solving this!

First grab this repo, and create an app on Heroku. We also set the PATH to the folder where the custom libs will be downloaded.

```
$ heroku create --buildpack https://github.com/ddollar/heroku-buildpack-multi.git
$ heroku config:add LD_LIBRARY_PATH=/app/lib
```

Now you can test that Xvfb works, by running my P5 library:

```
$ irb
$ > require 'bundler'
$ > Bundler.require
$ > sketch = P5::Sketch.new("/app/sketch", "/tmp/testbuild")
$ > sketch.run
$ > AWS::S3::Base.establish_connection!(:access_key_id => 'key', :secret_access_key => 'secret')
$ > AWS::S3::S3Object.store("grab.png", open("/tmp/grab.png"), 'mybucket ')
```

Boom! You now have a PNG generated from Processing on Heroku, sitting in your S3 folder.