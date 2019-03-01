Some notes on screen
=====

An example of screenrc file.
-----

Following is an sample example of screenrc file. You can keep the same as .screenrc at your home directory, or can keep at any place and later you can use ``-c`` options call the same.

::

    # don't show start up message
    startup_message off

    # auto detach on exit
    autodetach on

    # change ctrl-a to ctrl-x
    # escape ^Xx

    # allow scrolling
    termcapinfo xterm* ti@:te@

    # My status line
    #caption always "Screens: %{.bW}%-w%{.rW}%f%n %t%{-}%+w %=%{..G}  %{W}%Y-%m-%d %{W}%c %{g} %H"
    caption always "Screens: %{.bW}%-w%{.rW}%f%n %t%{-}%+w %=%{..G}  %{W}%Y-%m-%d %{W}%c %{g} %H"

    sorendition "kg"        # makes screen messages stand out, black on green
    altscreen on            # full-screen programs (less, Vim) should be cleared once quit
    vbell off               # visual bells are hard to do right. screen's isn't good
    defutf8 on              # allow utf characters

    # Set default lines of scrollback.
    defscrollback        9000            # default: 100
    ignorecase on           # case insensitive search in scroll-back mode

    bufferfile $HOME/.screen-exchange  # keep the buffer exchange file out of /tmp

    # Do NOT display copyright notice on startup.
    startup_message       off             # default: on

    hardstatus alwayslastline
    hardstatus string '%{= kw}[ %{= kb}%H%{= kw} ][%= %{= kw}%?%-Lw%?%{= kW}%n*%f %t%?%?%{= kw}%?%+Lw%?%?%= ][ %{r}%l%{w} ]%{w}[%{r} %d/%m/%y %C %A %{w}]%{w}'


How to use the screenrc file
-----
By default, the screen will read the file at ~/.screenrc, but you can keep the same configuration at your own place and you can use the same.

``screen -c /path/to/your/screenrc -S NameOfYourScreenSession``

You can use ``screen -ls`` command to check your screen session and later you can use, ``screen -rd`` to attach to the same session.