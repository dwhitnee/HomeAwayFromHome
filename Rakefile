require 'rake'
require 'erb'

desc "link the dot files and directories into user's home directory"
task :install do
  replace_all = false

  Dir.chdir("dotfiles")
  Dir.glob("[^#]*[^~]").each do |file|
    dest = "#{ENV['HOME']}/.#{file}"

    if File.exist?( dest )
      if File.identical? file, dest
        puts "identical #{dest}"
      else
        puts "mv -f #{dest} #{dest}.orig"
        puts "ln -s #{file} #{dest}"
      end
    end

  end
  Dir.chdir("..")

  Dir.glob('*[^~]').each do |file|
    next if %w[dotfiles Rakefile README.md LICENSE].include? file
    dest = "#{ENV['HOME']}"
    puts "ln -s #{file} #{dest}"
  end
end

=begin
  Dir['*'].each do |file|
    next if %w[Rakefile README.* LICENSE].include? file

    if File.exist?(File.join(ENV['HOME'], ".#{file.sub('.erb', '')}"))
      if File.identical? file, File.join(ENV['HOME'], ".#{file.sub('.erb', '')}")
        puts "identical ~/.#{file.sub('.erb', '')}"
      elsif replace_all
        replace_file(file)
      else
        print "overwrite ~/.#{file.sub('.erb', '')}? [ynaq] "
        case $stdin.gets.chomp
        when 'a'
          replace_all = true
          replace_file(file)
        when 'y'
          replace_file(file)
        when 'q'
          exit
        else
          puts "skipping ~/.#{file.sub('.erb', '')}"
        end
      end
    else
      link_file(file)
    end
  end
=end


def replace_file(file)
  filename = "$HOME/.#{file.sub('.erb', '')}"
  system %Q{mv -f #{filename} #{filename}.bak }
  link_file(file)
end

def link_file(file)
  if file =~ /.erb$/
    puts "generating ~/.#{file.sub('.erb', '')}"
    File.open(File.join(ENV['HOME'], ".#{file.sub('.erb', '')}"), 'w') do |new_file|
#      new_file.write ERB.new(File.read(file)).result(binding)
    end
  else
    puts "linking ~/.#{file}"
#    system %Q{ln -s "$PWD/#{file}" "$HOME/.#{file}"}
  end
end
