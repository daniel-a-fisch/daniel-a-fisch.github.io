source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!

gem "github-pages", group: :jekyll_plugins

# If you want to use Jekyll native, uncomment the line below.
# To upgrade, run `bundle update`.

# gem "jekyll"

gem "wdm", "~> 0.1.0" if Gem.win_platform?

# Plugins. These must match the `plugins:` list in _config.yml. They all ship
# inside the github-pages gem, but are listed explicitly so `bundle exec jekyll
# build` behaves the same way locally as it does on GitHub Pages.
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  # Powers the `redirect_from:` front matter that keeps previously indexed URLs
  # (/about/, /portfolio/, /publications/, /resume) working.
  gem "jekyll-redirect-from"
end
