# frozen_string_literal: true

source "https://rubygems.org"
#gemspec
group :jekyll_plugins do
    gem "jekyll-feed"
    gem "jekyll-seo-tag"
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
    gem "tzinfo", "~> 1.2"
    gem "tzinfo-data"
  end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.0", :install_if => Gem.win_platform?

# kramdown v2 ships without the gfm parser by default. If you're using
# kramdown v1, comment out this line.
gem "kramdown-parser-gfm"
#gem "jekyll", ENV["JEKYLL_VERSION"] if ENV["JEKYLL_VERSION"]
#gem "kramdown-parser-gfm" if ENV["JEKYLL_VERSION"] == "~> 3.9"
