source 'https://rubygems.org'

gemspec

gem 'sinatra', require: nil
gem 'rack', '~> 3.2.1'
# Local paths for forks with unpushed commits (revert to github develop pins once pushed)
gem 'reel', path: '../reel'
gem 'reel-rack', path: '../reel-rack'
gem 'ruby_ami', github: "logicsys/ruby_ami", branch: "develop"
gem 'baby_squeel', github: "logicsys/baby_squeel", branch: "develop"
gem 'blather', github: "logicsys/blather", branch: "develop"
gem 'celluloid', path: '../celluloid'
gem 'celluloid-io', path: '../celluloid-io'


group :test do
  # TODO: some expectations started failing in 3.8.3
  # The be_a_kind_of matcher requires that the actual object responds to either
  # #kind_of? or #is_a? methods  but it responds to neigher of two methods.
  gem 'rspec-expectations', '~> 3.13.5'
end
