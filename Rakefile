require 'semver'

desc "Builds IRCCloud OSX app"
task :build do
  version = SemVer.find
  sh "macgap build --name IRCCloud --version #{version} irccloud"
end

desc "Opens the app"
task :open do
  sh "open IRCCloud.app"
end

desc "Installs the app to User's Applications"
task :install => :build do
  dir = [ENV['HOME'], 'Applications'].join File::SEPARATOR
  directory dir
  FileUtils.cp_r "IRCCloud.app", dir, remove_destination: true
end

desc "Release the app to Github Release Archive"
task :release => :build do
  version = SemVer.find
  tool = "github-release"
  stdargs = "-r irccloud.app -t #{version}"
  archive = "IRCCloud.app-#{version}.zip"

  sh "zip -rq9 #{archive} IRCCloud.app"
  sh "#{tool} release #{stdargs}"
  sh "#{tool} upload #{stdargs} -n 'IRCCloud.app-#{version}.zip' -f #{archive}"
  sh "#{tool} info #{stdargs}"
end

task :default => :build
