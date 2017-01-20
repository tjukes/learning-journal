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
