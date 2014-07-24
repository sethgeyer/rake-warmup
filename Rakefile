desc "print a nice greeting"
  task :greet do
    puts "Whats your name"
    x = STDIN.gets.chomp()
    puts "hello #{x}"
  end

task :show_time do
  puts Time.now
end

desc "prints the persons favorite food from the environment file"
task :print_favorite_food do
  ENV["FAVORITE FOOD"] = "pineapple"
  x= ENV["FAVORITE FOOD"]
  puts "My favorite food is #{x}"
end

task :first do
  puts "First!"
end

task second: :first do
  puts "Second!"
end

task :wake_up do
  puts "Get your ass out of bed"
end

task :eat_breakfast do
  puts "Eat fruit loops"
end

task :brush_teeth do
  puts "Brush your yellow teeth"
end

task :ready_for_class => [:brush_teeth, :eat_breakfast, :wake_up] do
  puts "Goto School"
end

# namespace :this_thing do
  task :do_this do
    puts "this"
  end
# end



task :do_that do
  puts "that"
end


# task :other_ready => :do_this => :do_that do
# puts "now your other ready  "
# end


(task :default => "do_this")

