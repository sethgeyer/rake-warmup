## Introduction to Rake

Rake is a tool for writing Ruby code that performs automated commands for us.
The commands that rake knows how to execute are called **tasks**.
A few of the rake tasks we have seen to far:

- db:create
- db:migrate
- db:create_migration

One of Rake's best features is that it allows us to write regular Ruby code
rather than forcing us to learn a new syntax or language, unlike similar
tools in other languages.

So how does it work?

## Goals of this warmup

The main goals of this warmup are the ability to:

- write a simple rake task
- write a rake task that has a dependency on another rake task
- write a rake task that uses an environment variable

## Defining Tasks

You define rake tasks in a file called `Rakefile` in the root of your project.
Each rake task consists of a name and a block of Ruby code that runs when you execute
that rake task.

Tasks are defined using the `task` method.

    task :greet do
      puts "Hello there"
    end


To run a rake task, you run the `rake` command from the command line and
tell `rake` which task to execute. To run the `greet` task defined above, you
run:

    |ruby-2.1.1@gschool| Hunters-MacBook-Pro in ~/gschool/dev/warmups/rake-warmup
    ± |master ✗| → rake greet
    Hello there

Notice that `puts` in a rake task will print output to the terminal.

Now that you know the basic syntax, try writing some rake tasks of your own. Be sure
to add them to the Rakefile.

- Write a rake task that prints out the current time (check out the [Time](http://www.ruby-doc.org/core-2.1.2/Time.html) class)
- Change the `greet` task from above to ask for the user's name, then print "Hello, [name]"

## Task Descriptions

Rake provides a method called `desc` for describing what a rake task does.

    desc "Print a nice greeting"
    task :greet do
      puts "Hello there"
    end

When other developers read the tasks you write, they have a nice a summary of
what the task does. Another nice feature of using the `desc` method is that it
allows developers to see the summary of the rake tasks you write directly from
the command line, without having to look at the Rakefile itself.

After adding the desc line above the greet task, running `rake -T` looks like this:

    |ruby-2.1.1@gschool| Hunters-MacBook-Pro in ~/gschool/dev/warmups/rake-warmup
    ± |master ✗| → rake -T
    rake greet  # Print a nice greeting

Nice! This is especially helpful since sometimes rake tasks are defined in many different
files, and without `rake -T` you would have to go a track them down yourself.

Try running `rake -T` from the command line.

Do you see the rake tasks you wrote listed? Unless you added a desc to the tasks you wrote,
you won't see them listed by `rake -T`. The reason is that `rake -T` only lists rake tasks
that have a description. Add a desc to each of the rake tasks you have defined and run
`rake -T` again.

## Environment Variables



## Prerequisites

Sometimes you will have a rake task that depends on another rake task to run before
it can run. Rake allows us to define which tasks a given task is dependencies upon.
These dependencies are called prerequisites. Here is an example.

    task :first do
      puts "First!"
    end

    task :second => :first do
      puts "Second!"
    end

We want the `first` task to run before the `second` task. We tell rake about this
dependency when we define the second task with `:second => :first`. Here is what
happens when we run the `second` task.

    |ruby-2.1.1@gschool| Hunters-MacBook-Pro in ~/gschool/dev/warmups/rake-warmup
    ± |master ✓| → rake second
    First!
    Second!

Since the `second` task defined the `first` task as a prerequisite, the `first` task
runs before the `second` task is executed. Common usages of prerequisites include
loading required files or ensuring some condition is met before running a task.

- Write a rake task called `get_dressed` that depends on a rake task called `wake_up`

- Write a rake task called `ready_for_class`, that depends on tasks called `wake_up`,
`eat_breakfast`, and `brush_teeth`.

## Namespaces

Often you will have a set of rake tasks that are all related to one another. As an example,
think about all the database related rake tasks we have been using so far (db:create, db:migrate,
db:rollback, etc). With rake, you can create these kinds of related tasks using a namespace.

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

Here we have created two rake tasks, and since they are both related to greeting someone,
put them inside a namespace called `greeting`. To run these rake tasks, we have to specify the namespace.

    |ruby-2.1.1@gschool| Hunters-MacBook-Pro in ~/gschool/dev/warmups/rake-warmup
    ± |master ✗| → rake greeting:hello
    Hello there

    |ruby-2.1.1@gschool| Hunters-MacBook-Pro in ~/gschool/dev/warmups/rake-warmup
    ± |master ✗| → rake greeting:howdy
    Howdy partner

## Default Tasks

You can also

## Wrapping Up

You now know the basics of rake. That is all for this warmup, but
there is a lot more to rake. It is a powerful tool and this intro only touches
the surface.
