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


When you type `rake` at the command line, the `rake` program will look
makes some

The easiest way to define a rake

Tasks are defined using the `task` method.

    task :greet do
      puts "Hello there"
    end


## Task Descriptions

Rake provides a method called `desc` for documenting what a rake task does.

    desc "Print a nice greeting"
    task :greet do
      puts "Hello there"
    end

When other developers read the tasks you write, they have a nice a summary of
what the task does.

Another nice feature of using the `desc` method is that it allows developers
to see the summary of the rake tasks you write directly from the command line,
without having to look at the Rakefile itself.

- rake commands (-T, ...)
    - -T
    - --dry-run
    - --help to see all options
- namespaces
- environment variables
- prerequisites
- default tasks?
- anything else?
- only running a task one time
