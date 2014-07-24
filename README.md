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

- write a rake task that prints out the current time (check out the [Time](http://www.ruby-doc.org/core-2.1.2/Time.html) class)
- change the greet task from above to ask for the user's name, then print "Hello, [name]"

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

After adding the desc line above the greet task, running the `rake -T` looks like this:

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

## Prerequisites

Often times you will want one rake task to depend on another. Rake allows us to
define dependencies on tasks. These dependencies are called prerequisites,

    task :first do
      puts "First!"
    end

    task :second => :first do
      puts "Second!"
    end

Write a rake task called `ready_for_class`, that depends on tasks called `wake_up`,
`eat_breakfast`, and `brush_teeth`.

## Environment Variables


- default tasks?

## Wrapping Up

That is all for this warmup, but there is a lot more to rake. H
