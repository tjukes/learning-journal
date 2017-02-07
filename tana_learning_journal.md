# Learning Journal

## 15-01-2017 Learning more about my computer

* **Bash & shell**
  - Bash = "Bourne-again shell" `bash`, 1989
    - bash is a superset of the Bourne shell `sh`, 1977
    - Bourne shell is a rewrite / replacement for Thompson shell `sh`, 1971
  - Bash reference:  https://www.gnu.org/software/bash/manual/html_node/index.html#Top.  Good place to learn about how bash works - commands, command structure, execution, etc etc
  - Shell: is a command interpreter and a programming language
    - command interpreter provides utilities
    - programming language features allow these utilities to be combined
  - **Bash is the shell for the GNU OS**


* **GNU & Linux: Linux is the kernel, GNU is the OS**
  > A *kernel* is the part of the operating system that mediates access to system resources. It's responsible for enabling multiple applications to effectively share the hardware by controlling access to CPU, memory, disk I/O, and networking.  
  An *operating system* is the kernel plus applications that enable users to get something done (i.e compiler, text editor, window manager, etc).  
    *Source: http://stackoverflow.com/questions/2013937/what-is-an-os-kernel-how-does-it-differ-from-an-operating-system*



* **Linux distros**
  - Community-maintained or commercially backed
  - Debian is one of the earliest community-maintained versions, still active.  Ubuntu is a commercially backed distro (Canonical Ltd) based on Debian.
  - Other big ones: Fedora - commercially backed by Red Hat; Arch Linux - volunteer maintained, rolling release, for power users; Gentoo - compile from source code, for power users (Chrome OS is based on Gentoo); Slackware
  - Niche uses: Tails for privacy and anonymity; Android uses Linux kernel but lacks support for many GNU tools


* **Config files**
  - The "rc" at the end of config files means "run command" (or various other things depending on whose opinion is consulted)
  - A program's rc file is typically consulted every time the program starts; programs can be configured to consult their rc file periodically while running to check for changes


-------------------------

## 17-01-2017 Learning more about the tech world

* **Unix**
  - Base/inspiration for Linux, BSD (Berkeley Software Distribution), macOS, & Chrome/Chromium OS
  - Developed at Bell Labs


* **Ken Thompson**
  - "Compuing pioneer" of lots of important things:
    - C (and previously B)
    - Unix
    - refused to work on C++ because he thought it was inconsistent
    - UTF-8
    - regex
    - Plan 9 & Inferno
    - Go programming language (at Google)
  - At Bell Labs from 60s to 2000, then at Google


* **Bell Labs**
  > Researchers working at Bell Labs are credited with the development of radio astronomy, the transistor, the laser, the charge-coupled device (CCD), information theory, the operating systems Unix, Plan 9, Inferno, and the programming languages C, C++, and S. Eight Nobel Prizes have been awarded for work completed at Bell Laboratories.

  - As of late 2000s, no longer focusing on "pure" research in physics etc - shifting to "more immediately marketable areas, including networking, high-speed electronics, wireless networks, nanotechnology and software."


  -------------------------

## 18-01-2017 Revisiting Ruby

Info from ruby-doc.org

* **OOP** Compared to programming in a low-level language like C, which gets quite messy quite easily.  In C, data is passive.  In Ruby/OOP, data is "active" - objects are "machines" with interfaces (switches & dials) that allow us to ask them how to manipulate themselves, rather than manipulating them directly from outside (which is dangerous - eg directly assigning an arbitrary value to an odometer).  In OOP, an odometer knows what it is and takes care of running itself by processing input from the outside world (eg start point and end point).  


* **Inheritance structure** Subclasses get all the methods of their superclasses "for free", but they can be overwritten in specific circumstances where they need to be different (eg, Birds can fly, Penguins are Birds but cannot fly).  This is called *differential programming* (programming the differences).  
  - Redefine methods from a superclass: simply define again in subclass
  - Enhance/extend methods from a superclass: define again, but call "super" within def. If the superclass' method takes parameters, the extended subclass method can pass in pre-set arguments.  


* **Singleton methods** Each instance of a class behaves according to its class definition - unless any given method/property is overwritten on a particular instance. Eg, class Bird can have instances *flamingo*, *chickadee*, *troglodyte pacificus*, *penguin*. All of them have the "fly" method, except the *penguin*, whose "fly" method has been overwritten (eg to return something about swimming).  In other languages (eg C), instead of defining/overwriting a method directly on an instance of a class, a whole new class would have to be defined in order to create one instantiation.  
>A method given only to a single object is called a singleton method.


* **Modules** Modules are like classes, except that they cannot have subclasses or instances.  They are typically used to collect related methods and constants in a central location (eg, the Math module).
  - Access module constants and methods using `::` -- eg, `Math::PI`
  - Or access by using `include` to include the module directly in whatever scope you're currently in
  - **Modules are also used as mixins:** Ruby does not allow multiple inheritance; in order to add another set of methods etc to a (sub)class that already inherits from a class, you can `include` a module.  That leads to being able to access its methods & constants directly.
  Eg:
  ```
    Math::PI   gives 3.14....
    Or,
    include Math
    then
    PI   gives 3.14...
    So if Math was included in the Bird class, you could have
    Bird.PI   would give 3.14...
  ```


* **Procs / Procedure objects** These are named functions that can be called (`named_thing.call`), or passed to other functions/methods as arguments.  


* **Variables**
  >The first character of an identifier categorizes it at a glance:
    `$`	global variable, `@`	instance variable,  `[a-z] or _`	local variable,  `[A-Z]`	constant


* **Private vs protected methods** Private methods can never be called with an explicit receiver (ie, self.private_method).  They can be called with 'self' as an implicit receiver, by the class that the private method was defined on or any of its subclasses (ie, call without `self.`).  
Protected methods can be called with an explicit receiver, but only by the class they are defined on or its subclasses (ie, can call with or without `self.`)
  > Source: http://www.skorks.com/2010/04/ruby-access-control-are-private-and-protected-methods-only-a-guideline/ and http://weblog.jamisbuck.org/2007/2/23/method-visibility-in-ruby


-------------------------

## 20-01-2017 RVM: re terminal and bash

**Current issue: "PATH is not properly set up" / "RVM is not a function"**

* Error message:

```
Warning! PATH is not properly set up, '/home/tanaryder/.rvm/gems/ruby-2.3.1/bin' is not at first place,
         usually this is caused by shell initialization files - check them for 'PATH=...' entries,
         it might also help to re-add RVM to your dotfiles: 'rvm get stable --auto-dotfiles',
         to fix temporarily in this shell session run: 'rvm use ruby-2.3.1'.

RVM is not a function, selecting rubies with 'rvm use ...' will not work.

You need to change your terminal emulator preferences to allow login shell.
Sometimes it is required to use `/bin/bash --login` as the command.
Please visit https://rvm.io/integration/gnome-terminal/ for an example.
```

* Tried `rvm get stable --auto-dotfiles`: happily reloaded, but didn't fix the issue.


* Have not tried `rvm reset` as it looks like it might be necessary to go through the full set-up process again. This may be the next step though.


* RVM docs suggest that it may be related to a login shell (reads bash_profile) vs a non-login shell (just reads bashrc): https://rvm.io/support/faq#what-shell-login-means-bash-l


* Tried adding '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' (loading RVM as a function) as per http://stackoverflow.com/questions/18276701/getting-warning-path-is-not-properly-set-up-when-doing-rvm-use-2-0-0-defaul/18278735#18278735.  Also tried adding that to the bottom of zshrc.  No luck in changing $PATH.  


-------------------------

## 21-01-2017 Ruby version management :RVM vs rbenv vs chruby

* **RVM:** Manages Ruby downloads, switching between Ruby versions, and gems & gemsets.  Apparently the most frustrating option but also the most used and also the most powerful.

* **rbenv:** Manages switching between Ruby versions. Plugins handle Ruby installs and gem & gemset management.  Awesome overview of how it works by the guy who made it: http://stackoverflow.com/a/9422296

* **chruby**: Manages switching between Ruby versions, nothing else. Commonly used with another application that handles Ruby downloading.  Nothing built in to handle gems/gemsets, but apparently Bundler can handle virtually all of that.


-------------------------

## 23-01-2017 Re-intro to Rails (5) (API mode)

* To initialize a new API, just run `rails new app_name --api`.  Can also set the database to be postgres instead of allowing the initial setup with sqlite3 (the default) and then changing it afterwards: `rails new app_name --api --database=postgresql`.

* API mode cuts out everything to do with the views, but keeps taking care of things in the middle (most middleware remains).


## RSpec vs Minitest

* Apparently, most testing frameworks can/should be able to do all the same things... (some make certain things easier or more streamlined)

* Minitest comes by default with Rails. Technically, it just creates another Ruby class.

* RSpec has a DSL.  Means that tests "read like English", but obfuscates the way the testing works (method visibility? can it go in a module? inheritance?).

* RSpec makes it easy to re-run failing tests by printing out the line numbers of the failed test. If a test gets refactored, though, all the line numbers change which breaks the call to a specific line.

* RSpec's DSL lends itself well to BDD

* Minitest has two DSLs (assertive vs BDD)

* RSpec output is coloured; Minitest output is not. But there's a gem for that.

* Minitest ships with Rails, but the docs for each recommend different naming & test-writing conventions...?


## Building a Rails app

* `rails new` creates app foundation
* `rails db:setup` initializes database/s
* `rails g migration` & `rails db:migrate` sets up db tables
* `rails g model` creates models
* `rails g controller` creates controllers (which take care of actions/routes: `new` creates, `update` edits, etc)
* seed data primes the database for testing (and demoing).


-------------------------

## Testing

For now, Rails 5 (API-specific if possible), Ruby 2.3.1, Minitest
http://edgeguides.rubyonrails.org/testing.html

*NOTE: Testing philosophies are a controversial part of programming. DHH now advocates for system testing instead of dogmatic unit testing TDD. Most seem to agree that your testing practices should help you write better code and build better applications; different philosophies will help some people with their workflow/thinking flow more than others...*

*Test things that are likely to break. Don't test things that are likely to change (eg views). Test complex things. Test conditional things.*

* Test stubs are automatically generated with `rails g model (...)`
* Tests are stored in the `test` directory by default, which corresponds to the app's file directory
* "Test cases" and "tests": the class `Minitest::Test` is the superclass of `ActiveSupport::TestCase`. Anything that inherits from the ActiveSupport class is a "test case". More simply named "tests" are methods defined in classes that inherit directly from the Minitest class, that have names starting with `test_` (eg, `test_valid_password`). These will be run automatically when the test case is run.
  * Note - two different options for defining tests:
      ```
      test "the truth"
          assert true
      end
      ```
    is the same as
      ```
      def test_the_truth
          assert true
      end
      ```
* The assertion part validates an object or expression for expected results: http://edgeguides.rubyonrails.org/testing.html#available-assertions, http://edgeguides.rubyonrails.org/testing.html#rails-specific-assertions
* When printing test results, framework-related parts of the stack trace are not shown by default. Use the `-b` flag to display them: `bin/rails -b test/models/some_test.rb`
* Can run all tests (`bin/rails test`), tests in a specific directory (`bin/rails test test/models`), or a specific test file or a single specific test by specifying the line number in the file
* For help: `bin/rails test -h`
* **Fixtures:** sample data for testing, **vs** seed data - real data that persists to the database (eg the first admin account needed to manage the app).
  * Fixture stubs are created when Rails generates a model.
  * One fixture file per model.
  * Written in YAML.
  * They're cool.
  * Can use ERB when writing fixtures, for example to generate a thousand users at a time without writing out 1000 identities.
  * Fixtures are instances of Active Record. Can access the object directly - scope local to test case.
  * Deets here:  http://edgeguides.rubyonrails.org/testing.html#the-low-down-on-fixtures
* "Integration testing": testing the flow-through of the app - eg, sending a GET request to a route and checking for a success response and/or specific content on the page; sending a POST request, following the redirect, and checking to see that the new content is on the follow-up page.
* "Functional tests" for controllers: test how they handle incoming requests and that they respond appropriately. Test stubs are created when running `rails generate scaffold_controller (...)`
  * Hashes available after a request processed: `flash`, `cookies`, `session`
  * Instance variables available: `@controller` that is processing the request, the `@request` object, the `@response` object
  * Can create test helpers, eg login helper
* Testing routes - no details in main guide, find at http://api.rubyonrails.org/classes/ActionDispatch/Assertions/RoutingAssertions.html


-------------------------

## 24-01-2017 Git mastery

* **Merging vs rebasing:**
  * Good explanation - summary points follow:  https://medium.com/@porteneuve/getting-solid-at-git-rebase-vs-merge-4fa1a48c53aa#.kfyo9dzcd
  * **Merging** defaults to `ff`: if no changes have been made on master, the HEAD pointer is simply moved to the latest commit of the branch being merged in. It becomes as if there never was a separate branch. //According to the article, this is good for quick fixes that don't really need to have a standalone branch documenting their history for eternity. NOT GOOD for feature branches that add a coherent group of commits: this is the kind of history you do want to keep (similar effect to pull requests).
  * Can merge with `--no-ff` to force git to keep the branch history. Also creates a separate merge commit with its own commit message.
  * **Rebasing:** For cleaning up history. Eg:
    * Feature branch was created a while ago but not finished, master has advanced a lot --> rebase to replay old commits of feature branch on top of updated master before continuing to work on feature branch.
    * Local branch (not pushed to remote) has messy history --> rebase to clean it up before merging or pushing to remote. Squash, reorder, split, remove, reword, fixup, etc. Do this to keep the history readable and useful, rather than blindly keeping everything out of paranoia.
* **Commit messages:** Lots of guidelines out there (http://chris.beams.io/posts/git-commit/, https://www.git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#Commit-Guidelines); most importantly, be aware of the guidelines for each project (or organization).

* **Introducing other people to Git:**
  * TODO: Find good resources that are accessible, are useful & actionable (have commands/instructions), point people in the right direction (don't include bad practices), and do a good job of highlighting the importance of git
  * Resources so far:
  * Jen's git diagram from LHL: good for initial setup, doesn't touch on process after repo setup
  * git-scm book: excellent excellent... but quite detailed, not necessarily an easily accessible/persuasive starter piece
  * The Simple Guide - No Deep Shit: not bad as a reference for commands, but not good re actual use practices
  * William's "Git Rules" summary from LHL - not bad, needs context & explanation (ie not a starter):
    - *One thing per commit*
    - *Commit messages explain what, why, and what it means (no such thing as too much explanation)*
    - *No fixup commits (use amend or interactive rebase)*
    - *Descriptively named feature branches*
    - *Code goes into master via pull requests*
    - *Pull requests get code reviewed and _closed_ (not edited) if they aren't up to snuff*


## Model testing

> To get started, a model spec should include tests for the following:
>
> - the default factory should generate a valid object (more on factories in just a moment)
> - data that fail validations should not be valid
> - class and instance methods perform as expected
>
> Source: https://everydayrails.com/2012/03/19/testing-series-rspec-models-factory-girl.html


## Single table inheritance / STI

Idea: a quick google suggests that this structure may be more common (and maybe mroe useful?) than implied by some during our LHL final project. I can use the rewrite as an opportunity to learn more about what it really involves - when is it truly a good/bad idea, what becomes more complicated, what becomes simpler/more functional/more efficient, what are the best practices.

A couple starting points:
- http://stackoverflow.com/questions/tagged/single-table-inheritance
- http://stackoverflow.com/questions/4507149/best-practices-to-handle-routes-for-sti-subclasses-in-rails
- http://stackoverflow.com/questions/15853334/rails-create-scaffold-for-models-to-inherit-from-superclass
- http://stackoverflow.com/questions/604870/can-i-do-sti-and-still-use-polymorphic-path-helpers/605172#605172
- http://stackoverflow.com/questions/555668/single-table-inheritance-and-where-to-use-it-in-rails


-------------------------

## Computer info & upgrading

* Upgrading SSD:
  * Get an **M.2 42mm SSD**
  * MyDigitalSSD - problems with firmware versions 1.5 & 1.6 fixed now?
  * Transcend
  * ZTC

* Command to find processor: `cat /proc/cpuinfo | grep 'model name' | uniq`
  * Chilo has: `model name	: Intel(R) Celeron(R) 2957U @ 1.40GHz`
  * "The CPU in the C720 Celeron is at the high end of standard Chromebook options" - https://www.reddit.com/r/GalliumOS/comments/5k7ek2/looking_for_a_highly_portal_laptop_with_crazy/dbm9q0u/


-------------------------

## 31-01-2017 Ruby reminders

* Initializing multiple variables on the same line:
  * `foo = bar = "this string"`: works, but both variables will point to the same memory address (`foo.object_id` is identical to `bar.onject_id`)
  * `foo, bar = 0, 1`: works; make sure to assign a value to every variable - if `foo, bar = 0`, then `foo` will be initialized (as 0) but not `bar` (will be `nil`)
* Ranges:
  * `1..5` means 1, 2, 3, 4, 5 (two dots .. includes start and end points of range)
  * `1...5` means 1, 2, 3, 4 (three dots ... includes start point but excludes end point)
* `Prime`: the set of all prime numbers
* Array methods:
  * `.transpose`: assumes 'self' is an array of arrays, and transposes the 'rows' and 'columns' - `[[1, 2], [23, 12], [58, 90]]` becomes `[[1, 23, 58], [2, 12, 90]]`
  * `.zip`: http://apidock.com/ruby/Array/zip


## Currying

Breaking down a function that takes multiple arguments into a series of functions that each take one argument -  http://stackoverflow.com/a/36321/5500952. Excellent explanation halfway down this article (https://www.sitepoint.com/functional-programming-techniques-with-ruby-part-ii/), after explanation of methods blocks procs lambdas (see notes below)

* **Partial function application** differs from currying: calling a function with some number of arguments, in order to get a function back that will take that many fewer arguments

* `Proc#curry` curries a function for you:
  * define a function `first_func` taking multiple arguments (eg lambda)
  * then create a new function that takes the first argument expected by `first_func`: `second_func = first_func.curry(pass_arg_here)`

* Methods, blocks, procs, and lambdas: https://www.sitepoint.com/functional-programming-techniques-with-ruby-part-ii/
  * All four are really variations of procs (syntactic sugar for procs, or can be made to behave like procs):
    * methods are not really meant (?) to be passed around
    * blocks are but in a limited way - they aren't named
    * procs can be named and easily passed around
    * lambdas have two specific differences - see next points
  * Lambdas check the arguments they are given (ArgumentError if given one, expecting two)
  * Lambdas containing a `return` statement will not cause the method calling the lambda to return. Procs will.
  * Procs are tied to the scope they're created in - they will still have access to local variables even when they are called somewhere else.

* **Higher order functions** do one of the following:
  * Accept a function as an argument
  * Return a function as a return value


-------------------------

## 01-02-2017 Dev setup recovery

*Less of an explanation of what was learned, than a reminder of what was done...*

* Replaced RVM with rbenv
  * Remember why: configuration/setup/ongoing use of RVM was troublesome and complicated -- not necessarily impossible, just seemed like maybe more of a headache than it was worth. This switch is an experiment. I can always go back to RVM`
  * RVM removal process: `rvm implode` and then manually remove mention of RVM from allll the dotfiles: .bashrc, .bash_profile, .profile, .zshrc, .zlogin, AND MORE -- needed to check them all
  * rbenv installation process documented in the setup script on Github


* Advanced the dev setup recovery "script" a few steps:
  * Made copies of important dotfiles / config files: not sure if I got everything, but hopefully the key pieces. Should check again before wiping computer.
  * Made copies manually, committing to repo on Github instead of initializing locally.
  * **Previous point prompted the search that was finally effective! RECONSIDER THIS STRATEGY in light of the following:**
    * http://blog.smalleycreative.com/tutorials/using-git-and-github-to-manage-your-dotfiles/
    * http://dotfiles.github.io/
  * Added a few more details & tidbits to the central "script" (not really a script yet, mostly a scratchpad with reminders and a few commands)


## Continuing with Pedalspacecadet

*Same type of entry as above...*

Went ahead and started trying to write tests along with the models I was writing. More challenging than anticipated:
* Needed to re-install gemset (and first re-install bundler) after the rvm-to-rbenv adventure
* Forgot that when creating the Cyclist & Mechanic, if using `rails g scaffold`, migrations would be created: bad; both these models should talk to the User table and not have their own
* Encountered a strange error in AR when trying to run the basic tests (a simple one I wrote plus all the stock ones): `ActiveRecord::RecordNotUnique: PG::UniqueViolation: ERROR:  duplicate key value violates unique constraint "users_pkey"` for each of the 16 tests. *To be continued...*


-------------------------

## Testing

Points from https://semaphoreci.com/blog/2014/01/14/rails-testing-antipatterns-fixtures-and-factories.html

* Fixtures vs factories: fixtures are apparently not so cool.
  * Factory Girl (with RSpec) lets you create test data within the tests. With fixtures, record-creation happens in a separate file: makes it hard to know why you are testing for what in any given test. Updates have to happen manually in two different places.
  * Factories can create too much data / too many associations: calling one factory may silently create many associated records (eg, creating a comment on a post also creates the post). Beware creating too many extra records w factories just because you can. Also avoid adding unnecessary detail to records when testing them (eg, testing a user's name doesn't require the presence of a phone number)
  * Fixtures bypass ActiveRecord when creating records: ie, model validations aren't called.
  * Fixtures load records into db before tests are run: sometimes this is useful (accessing things already in db), sometimes it is not (in more complex situations, difficult to test specific situations when lots of data already present?)
  * On the other hand, Factory Girl can be slower in tests that actually hit the db


-------------------------

## 05-02-2017 Pedalspacecadet: PG error (`PG::UniqueViolation`)

* StackOverflow post has some extra details of the situation and what I've tried so far: http://stackoverflow.com/questions/42011612/postgres-rails-5-auto-assigning-primary-key-that-already-exists-during-testing

* Have tried:
  *
    ```
    SELECT setval('users_id_seq', (SELECT max(id) FROM users));
    ```
    \- Run from direct connection with db (command sequence: `psql`, `\connect pedalspacecadet_test` (from memory, may not be exact))

  *
    ```
    ActiveRecord::Base.connection.tables.each do |t|
      ActiveRecord::Base.connection.reset_pk_sequence!(t)
    end
    ```
    \- Run from rails console (`bin/rails c test`)

  * 
    ```
    -- Login to psql and run the following
    -- What is the result?
    SELECT MAX(id) FROM your_table;
    -- Then run...
    -- This should be higher than the last result.
    SELECT nextval('your_table_id_seq');
    -- If it's not higher... run this set the sequence last to your highest pid it.
    -- (wise to run a quick pg_dump first...)
    SELECT setval('your_table_id_seq', (SELECT MAX(id) FROM your_table));
    -- if your tables might have no rows
    -- false means the set value will be returned by the next nextval() call    
    SELECT setval('your_table_id_seq', COALESCE((SELECT MAX(id)+1 FROM your_table), 1), false);
    ```
    \- Notes: second command resulted in a lower value; did not do a pg_dump (unnecessary to back up a test database esp before any tests are working); then ran the last command since the test database should have no rows

  * Re-cloning the repo into a fresh dir, running bundle install and db:setup and re-running the tests: same error (expected)
  * Connecting to psql and running `INSERT INTO ...` to create records: the proper IDs are assigned, in order.
  * In rails console (`bin/rails c test`), running `User.create`: the proper IDs are assigned in order. Same with `User.new` (when record is saved).
  * Adding a uniqueness validation to the User model for the `id` column. Seemed crazy; surprise, it didn't work.
  * Replacing `.new` with `.create` in the test. No change.
  * This version of resetting the sequence: https://wiki.postgresql.org/wiki/Fixing_Sequences. No change.


* About PG sequences: http://www.neilconway.org/docs/sequences/
  * A 'sequence object'  is created for every field that needs an autoincrementing value -- a **serial** value: ie, every primary key (id). PG handles this automatically but it can be seen after running the migration (I think that's where I saw it).


* Trying more things: Created a "blank slate" testing app and have so far discovered:
  * Tests run fine with no STI
  * Tests run fine (in the blank slate app) with the Users table set up for STI (ie, first column is a `type` column), but error out as soon as the scaffolding is generated for the first sub-type. (*Note, different error:* `ActiveRecord::StatementInvalid: PG::UndefinedTable: ERROR:  relation "snurks" does not exist` makes sense because yb default, a model is expected to have its own table in the db). When the subclass is made to inherit from the superclass (ie, the model definition reads `class Snurk < User`), the errors change the familiar error (PG::UniqueViolation with 980190962 for primary key)
  * Rails 5 notes:
    * Deprecation warnings from using Rails 5 with Ruby 2.4.0 (Fixnum/Bignum deprecated) are fixed in Rails 5.0.2
    * Can set a specific branch to get a gem from in gemfile like so: `gem 'rails', github: "rails/rails", branch: '5-0-stable'` -- this didn't work to pull down 5.0.2 yet though, maybe still too recent?


* TO TRY:
  * Use RSpec instead of Minitest
  * Use Ruby 2.3 or 2.2
  * Use Rails 4.x
