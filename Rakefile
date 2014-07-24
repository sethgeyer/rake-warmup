namespace :greeting do
  desc "Say hello"
  task :hello do
    puts "Hello there"
  end

  desc "Say howdy"
  task :howdy do
    puts "Howdy partner"
  end
end

task :first do
  puts "First!"
end

task :second => :first do
  puts "Second!"
end
