require 'rake/extensiontask'
require 'rubygems/package_task'

Rake::ExtensionTask.new 'my_malloc' do |ext|
  ext.lib_dir = 'lib/my_malloc'
end

s = Gem::Specification.new 'my_malloc', '1.0' do |s|
  s.summary = 'my malloc wrapper'
  s.authors = %w[a]
  s.extensions = %w[ext/my_malloc/extconf.rb]
  s.files = %w[
    MIT-LICENSE
    Rakefile
    ext/my_malloc/extconf.rb
    ext/my_malloc/my_malloc.c
    lib/my_malloc.rb
  ]
end

Gem::PackageTask.new s do
end

task test: %w[compile] do
  ruby '-Ilib', '-rmy_malloc', '-e', 'p MyMalloc.new(5).free'
end

task default: :test

