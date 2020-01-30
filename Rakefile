require "bundler"
Bundler::GemHelper.install_tasks

begin
  require "rspec/core/rake_task"

  task default: %i{spec style}

  begin
    require "chefstyle"
    require "rubocop/rake_task"
    desc "Run Chefstyle tests"
    RuboCop::RakeTask.new(:style) do |task|
      task.options += ["--display-cop-names", "--no-color"]
    end
  rescue LoadError
    puts "chefstyle gem is not installed. bundle install first to make sure all dependencies are installed."
  end

  desc "Run all unit specs in spec directory"
  RSpec::Core::RakeTask.new(:spec) do |t|
    t.pattern = "spec/unit/**/*_spec.rb"
  end

rescue LoadError
  STDERR.puts "\n*** RSpec not available. (sudo) gem install rspec to run unit tests. ***\n\n"
end
