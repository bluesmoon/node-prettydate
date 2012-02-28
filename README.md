prettydate
==========

This is a Node.JS module to pretty-print dates in a variety of standard formats.  It includes the ISO8601 and RFC2822
formats and a port of the <a href="http://yuilibrary.com/yui/docs/api/modules/datatype-date-format.html">strftime library</a>
that I wrote for YUI based on the Open Group specification defined at http://www.opengroup.org/onlinepubs/007908799/xsh/strftime.html
(not including modified conversion specifiers i.e., Ex and Ox).

introduction
------------

Most programming languages have access to a strftime function provided by the Open Group.  JavaScript, on the other hand, has a Date object
that gives you basic access to different parts of a date, but no single method to stringify dates using the common OG specification.  This
module attempts to correct that by being the most complete native JavaScript implementation of the Open Group spec.

It was originally written as a standalone module for client-side JavaScript, and then ported to become part of the YUI library.

This implementation returns to the original module, includes all the enhancements added as part of YUI and adds a few of its own.

why javascript and not c?
------------------------

On the client-side, one has no choice.  JavaScript is the only language available.  On the server-side though, one could easily just create
a binding for the strftime function provided by libc.  There are a few reasons not to do this though.

*  The C library deals with seconds while JavaScript dates count in milliseconds.  We try not to be lossy.
*  The C library available on a system may not necessarily implement all the format specifiers from the
   Open Group spec.
*  There may be some platforms that node works on that do not have a strftime function.
*  Lastly, we could easily take this JavaScript module to the client-side

synopsis
--------

    var strftime=require('prettydate').strftime;

    var d=new Date();
    console.log(strftime(d, "%c"));
    

installation
------------

    $ npm install prettydate
