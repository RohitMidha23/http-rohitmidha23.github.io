# Website

## Run

To run locally :

```bash
bundle exec jekyll serve --config _config.yml,_config-dev.yml
```

## Common Errors

Better to delete the `Gemfile.lock` before running bundle install. Consider adding `webrick` also separately (it's currently in `Gemfile`). Same with `rack`, but check the stackoverflow error once.

1. For Webrick error:
   https://github.com/jekyll/jekyll/issues/8523#issuecomment-751409319

Basically just run `bundle add webrick` (which updates the Gemfile)

2. For Rack error:
   https://stackoverflow.com/questions/75088199/require-cannot-load-such-file-rack-handler-loaderror

## Original Repo

https://github.com/sergiokopplin/indigo
