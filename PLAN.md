# How to split the repository

(Taken from "Re: [Wikitech-l] Version control" on wikitech-l)

In order to convert to Git it would help to collect a list of things
that should be split into separate repositories:

 * /USERINFO, /civicrm and /wikimedia-web
 * Everything in /trunk/*
 * Additionally /trunk/extensions/* and maybe some /trunk/tools/*

That should yield around 500 repositories. That might sound crazy but
best practice for any distributed version control system is that
repositories should be split at the boundaries at which code doesn't
pass over, and when's the last time /trunk/FOO shared some code with
/trunk/extensions/BAR for instance?

And if someone really wants to check out all 430 extensions that's
easy enough with an "extensions" project with 430 submodules, but the
most common case should be someone checking out MediaWiki.git + 3-5
extensions.

# Rewriting on commits

This is the sort of rewriting we'd like to do on comitts:

 * Rewrite the commits to give everyone real names / emails, like Tim
   Starling / tstarling@wikimedia.org instead of tstarling. This can be
   done automatically by parsing the USERINFO files & adding to them
   where appropriate.
 * Combine users like magnusmanske and magnus_manske into one

Both of the above are done using the
[mediawiki-userinfo](http://github.com/avar/mediawiki-userinfo)
script.

 * Use [git-svn-abandon](http://blog.woobling.org/2009/06/git-svn-abandon.html)

There's some really neat stuff there. I already used it for [the osm
website](http://github.com/avar/openstreetmap-website) conversion.

 * Rename/drop branches/tags if someone wants that

Lots of crap tags/branches nobody cares about probably. It would
probably be best to do this /after/ converting to Git.

