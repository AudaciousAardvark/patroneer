# typed: ignore
# frozen_string_literal: true

require "bundler/gem_tasks"
require "rake/testtask"

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList["test/**/test_*.rb"]
end

require "rubocop/rake_task"

RuboCop::RakeTask.new

desc "Generate the gem RBIs files"
task :tapioca do
  sh "bin/tapioca gem"
end

desc "Run the Sorbet typechecker"
task :sorbet do
  sh "bundle exec srb tc"
end

task default: %i[sorbet rubocop:autocorrect_all test]
