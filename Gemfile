source 'https://rubygems.org'

gemspec

gem 'sinatra', require: nil
gem 'rack', '< 3.0'  # Rack 3.0 incompatible with reel-rack 0.2.3
gem 'reel', github: "logicsys/reel", branch: "develop"
gem 'reel-rack', github: "logicsys/reel-rack", branch: "develop"


group :test do
  # TODO: some expectations started failing in 3.8.3
  # The be_a_kind_of matcher requires that the actual object responds to either
  # #kind_of? or #is_a? methods  but it responds to neigher of two methods.
  gem 'rspec-expectations', '< 3.8.3'
end
