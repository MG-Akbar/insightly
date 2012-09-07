require "rubygems"
require "spec/rake/spectask"
require "rake/rdoctask"

task :default => %w[spec:unit spec:integration]

task :dev_console do
  sh "irb -I lib -rubygems -r insightly -r env/development"
end

desc "Run units"
Spec::Rake::SpecTask.new("spec:unit") do |t|
  t.spec_files = FileList["spec/unit/**/*_spec.rb"]
end

desc "Run integration"
Spec::Rake::SpecTask.new("spec:integration") do |t|
  t.spec_files = FileList["spec/integration/**/*_spec.rb"]
end

task :gem do
  exec('gem build insightly.gemspec')
end

require File.dirname(__FILE__) + "/lib/insightly/configuration.rb"

desc 'Cleans generated files'
task :clean do
  rm_f Dir.glob('*.gem').join(" ")
  rm_rf "rdoc"
  rm_rf "bt_rdoc"
end
