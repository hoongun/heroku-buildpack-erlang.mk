# Heroku buildpack: Erlang
Heroku buildpack for Erlang apps using [erlang.mk](http://erlang.mk/). If you are using [Rebar](https://github.com/basho/rebar), you should try [this](https://github.com/heroku/heroku-buildpack-erlang.git) or [this](https://github.com/archaelus/heroku-buildpack-erlang.git).

### Configure your Heroku App::
  
    heroku config:add BUILDPACK_URL="https://github.com/hoongun/heroku-buildpack-erlang.mk.git" -a YOUR_APP

### Example of building a Heroku app
	cd YOUR_APP_DIR
  
    heroku login
	heroku apps:create YOUR_APP
	heroku git:remote -a YOUR_APP
  
	# Erlang buildpack
	heroku config:add BUILDPACK_URL="https://github.com/hoongun/heroku-buildpack-erlang.mk.git" -a YOUR_APP
  
	# Add a Procfile for launch an app
	echo "web: make run" > ./Procfile
  
	git commit -am "Added Procfile"
	git push heroku master

