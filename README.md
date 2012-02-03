## SYNOPSIS

    bloat-blame [options] binary

## DESCRIPTION

`bloat-blame` is a tool for working out how many bytes each line of source code
takes up in a C++ program.  It uses `addr2line` and `readelf` to parse debug
info.

## OPTIONS

 * `--extent [all|.text]`:
   Specifies which bytes within the binary should be analysed

## DEPENDENCIES

`bloat-blame` depends on:

 * [Python](http://python.org/)
 * addr2line - a part of [GNU binutils](http://www.gnu.org/software/binutils/)
 * objdump - also a part of [GNU binutils](http://www.gnu.org/software/binutils/)

## HOWTO

1. Build your program/library with debug info turned on:

        $ CFLAGS='-g' make

2. Run bloat-blame on the resulting binary:

        $ bloat-blame ./myprog

`bloat-blame` will output something like:

    22     src/main.c:22
    213    src/main.c:23
    7653   src/bloat.c:324

This is a list in ascending order of size.  The first column is the number of
bytes apportioned to the file/line in the second column.

## LICENSE

`bloat-blame` is Copyright (C) 2012 YouView TV Ltd. and is distributed under
the GNU General Public License version 2 or at your option any later version.
See the COPYING file for more information.  This licence was chosen to be
consistent with GNU binutils.
