desc "Builds IRCcloud OSX app"
task :build do
  sh "macgap build irccloud"
end

desc "Opens the app"
task :open do
  sh "open irccloud.app"
end

desc "Installs the app to User's Applications"
task :install do
  dir = [ENV['HOME'], 'Applications'].join File::SEPARATOR
  directory dir
  FileUtils.cp_r "irccloud.app", dir
end

task :default => :build
