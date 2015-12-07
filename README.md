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
	echo "web: ./_rel/YOUR_APP_release/bin/YOUR_APP_release-1 start && tail -f output.log" > ./Procfile
	git commit -am "Added a Procfile"

	# To set the version of OTP:
	echo otp_src_18.1 > .preferred_otp_version
	git commit -m "Selected the preferred OTP version" .preferred_otp_version

	git push heroku master

### Use "heroku-repo" for flush the buildpack CACHE_DIR
	heroku plugins:install https://github.com/heroku/heroku-repo.git
	heroku repo:purge_cache -a appname