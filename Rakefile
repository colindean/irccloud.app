desc "Builds IRCCloud OSX app"
task :build do
  sh "macgap build --name IRCCloud irccloud"
end

desc "Opens the app"
task :open do
  sh "open IRCCloud.app"
end

desc "Installs the app to User's Applications"
task :install => :build do
  dir = [ENV['HOME'], 'Applications'].join File::SEPARATOR
  directory dir
  FileUtils.cp_r "IRCCloud.app", dir
end

task :default => :build
