# Website


## Run 

To run locally :

```bash
bundle exec jekyll serve --config _config.yml,_config-dev.yml
```

## Common Errors

For Webrick error:
https://github.com/jekyll/jekyll/issues/8523#issuecomment-751409319

Basically just run `bundle add webrick` (which updates the Gemfile)

Better to delete the `Gemfile.lock` before running bundle install. Consider adding `webrick` also separately (it's currently in `Gemfile`).


## Original Repo 
https://github.com/sergiokopplin/indigo