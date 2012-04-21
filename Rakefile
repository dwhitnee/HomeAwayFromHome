# -*-ruby-*-
require 'rake'

#----------------------------------------
desc "link the dot files and directories into user's home directory"
task :install do
  replace_all = false

  Dir.chdir("dotfiles")
  Dir.glob("[^#]*[^~]").each do |file|
    dest = "#{ENV['HOME']}/.#{file}"

    if File.exist?( dest )
      replace_file( file, dest )
    else
      link_file( file, dest)
    end

  end
  Dir.chdir("..")

  Dir.glob('*[^~]').each do |file|
    next if %w[dotfiles Rakefile README.md LICENSE].include? file
    dest = "#{ENV['HOME']}/#{file}"

    if File.exist?( dest )
      replace_file( file, dest )
    else
      link_file( file, dest)
    end

  end
end

#----------------------------------------
# replace unless already identical file
#----------------------------------------
def replace_file( src, dest )
  if File.identical? src, dest
    puts "identical #{dest}, ignoring"
  else
    puts "mv -f #{dest} #{dest}.orig"
    # File.rename( dest, "#{dest}.orig" )
    link_file( src, dest )
  end
end

#----------------------------------------
# symlink unless dest is aleady a symlink
#----------------------------------------
def link_file( src, dest )
  if File.symlink?( dest )
    puts "#{dest} is already a symlink, ignoring"
  else
    puts "linking #{src} to #{dest} "
    # File.symlink( src, dest )
  end
end
