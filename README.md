hub: git + hub = github
=======================

`hub` is a command line utility which adds GitHub knowledge to `git`.

It can used on its own or as a `git` wrapper.

Normal:

    $ hub clone rtomayko/tilt

    Expands to:
    $ git clone git://github.com/rtomayko/tilt.git

Wrapping `git`:

    $ git clone rack/rack

    Expands to:
    $ git clone git://github.com/rack/rack.git

hub requires you have `git` installed and in your `$PATH`. It also
requires Ruby 1.8.6+ or Ruby 1.9.1+. No other libraries necessary.


Install
-------

### Standalone

`hub` is most easily installed as a standalone script:

    curl -s http://defunkt.github.com/hub/standalone > ~/bin/hub &&
    chmod 755 ~/bin/hub

Assuming `~/bin/` is in your `$PATH`, you're ready to roll:

    $ hub version
    git version 1.6.4.2
    hub version 0.3.2

### Homebrew

    brew install hub

### RubyGems

Though not recommended, `hub` can also be installed as a RubyGem:

    $ gem install git-hub

(Yes, the gem name is `git-hub`.)

(It's not recommended because of the RubyGems startup time. See [this
gist][speed] for information.)

### Standalone via RubyGems

Yes, the gem name is still `git-hub`:

    $ gem install git-hub
    $ hub hub standalone > ~/bin/hub && chmod 755 ~/bin/hub
    $ gem uninstall git-hub

### Source

You can also install from source:

    $ git clone git://github.com/defunkt/hub.git
    $ cd hub
    $ rake install prefix=/usr/local


Aliasing
--------

hub works best when it wraps `git`. This is not dangerous - your
normal git commands should all work. hub merely adds some sugar.

Typing `hub alias <shell>` will display alias instructions for
your shell. `hub alias` alone will show the known shells.

For example:

    $ hub alias bash
    Run this in your shell to start using `hub` as `git`:
      alias git=hub

You should place this command in your `.bash_profile` or other startup
script to ensure runs on login.

The alias command can also be eval'd directly using the `-s` flag:

    $ eval `hub alias -s bash`


Commands
--------

Assuming you've aliased `hub` to `git` the following commands now have
superpowers:

### git clone

    $ git clone schacon/ticgit
    > git clone git://github.com/schacon/ticgit.git

    $ git clone -p schacon/ticgit
    > git clone git@github.com:schacon/ticgit.git

    $ git clone resque
    > git clone git://github.com/YOUR_USER/resque.git

    $ git clone -p resque
    > git clone git@github.com:YOUR_USER/resque.git

### git remote add

    $ git remote add rtomayko
    > git remote add rtomayko git://github.com/rtomayko/CURRENT_REPO.git

    $ git remote add -p rtomayko
    > git remote add rtomayko git@github.com:rtomayko/CURRENT_REPO.git

    $ git remote add origin
    > git remote add origin git://github.com/YOUR_USER/CURRENT_REPO.git

### git init

    $ git init -g
    > git init
    > git remote add origin git@github.com:YOUR_USER/REPO.git

### git push

    $ git push origin,staging,qa bert_timeout
    > git push origin bert_timeout
    > git push staging bert_timeout
    > git push qa bert_timeout

### git browse

    $ git browse
    > open http://github.com/CURRENT_REPO

    $ git browse schacon/ticgit
    > open http://github.com/schacon/ticgit

    $ git browse -p schacon/ticgit
    > open http://github.com/schacon/ticgit

    $ git browse resque
    > open http://github.com/YOUR_USER/resque

    $ git browse -p resque
    > open https://github.com:YOUR_USER/resque

### git help

    $ git help
    > (improved git help)
    $ git help hub
    > (hub man page)


GitHub Login
------------

To get the most out of `hub`, you'll want to ensure your GitHub login
is stored locally in your Git config.

To test it run this:

    $ git config --global github.user

If you see nothing, you need to set the config setting:

    $ git config --global github.user YOUR_USER

See <http://github.com/guides/local-github-config> for more information.


Configuration
-------------

If you prefer `http://` clones to `git://` clones, you can set the
`hub.http-clone` option using `git-config`.

For example:

    $ git clone defunkt/repl
    < git clone >
    $ git config --global --add hub.http-clone yes
    $ git clone defunkt/repl
    < http clone >

Or you can enter this manually into your `~/.gitconfig` file:

    $ cat ~/.gitconfig
    [hub]
      http-clone = yes


Prior Art
---------

These projects also aim to either improve git or make interacting with
GitHub simpler:

* [eg](http://www.gnome.org/~newren/eg/)
* [github-gem](http://github.com/defunkt/github-gem)
* [gh](http://github.com/visionmedia/gh)


Contributing
------------

Once you've made your great commits:

1. [Fork][0] hub
2. Create a topic branch - `git checkout -b my_branch`
3. Push to your branch - `git push origin my_branch`
4. Create an [Issue][1] with a link to your branch
5. That's it!


Meta
----

* Code: `git clone git://github.com/defunkt/hub.git`
* Home: <http://github.com/defunkt/hub>
* Bugs: <http://github.com/defunkt/hub/issues>
* List: <http://groups.google.com/group/github>
* Test: <http://runcoderun.com/defunkt/hub>
* Gems: <http://gemcutter.org/gems/git-hub>


Author
------

Chris Wanstrath :: chris@ozmm.org :: @defunkt

[0]: http://help.github.com/forking/
[1]: http://github.com/defunkt/hub/issues
[speed]: http://gist.github.com/284823
