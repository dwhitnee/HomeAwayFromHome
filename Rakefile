# -*-ruby-*-
require 'rake'

#----------------------------------------
desc "link the dot files and directories into user's home directory"
task :install do
  replace_all = false

  Dir.chdir("dotfiles")
  Dir.glob("[^#]*[^~]").each do |file|

    src  = "#{ENV['PWD'] }/dotfiles/#{file}"
    dest = "#{ENV['HOME']}/.#{file}"

    if File.exist?( dest )
      replace_file( src, dest )
    else
      link_file( src, dest)
    end

  end
  Dir.chdir("..")

  Dir.glob('*[^~]').each do |file|
    next if %w[dotfiles Rakefile README.md LICENSE].include? file
    src  = "#{ENV['PWD'] }/#{file}"
    dest = "#{ENV['HOME']}/#{file}"

    if File.exist?( dest )
      replace_file( src, dest )
    else
      link_file( src, dest)
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
    puts "mv #{dest} #{dest}.orig"
    File.rename( dest, "#{dest}.orig" )
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
    puts "ln -s #{src} #{dest} "
    File.symlink( src, dest )
  end
end
