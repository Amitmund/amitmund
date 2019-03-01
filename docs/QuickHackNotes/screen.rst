Some notes on screen
=====

An example of screenrc file.
-----

Following is an sample example of `screenrc` file. You can keep the same as `.screenrc` at your home directory, or can keep at any place and later you can use ``-c`` options, to use your `screenrc` file.

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


To see the shared screen session
-----

You can use ``screen  -rx -S ScreenSession`` to see the terminal at the same time.


Few screen options
-----

::


    ``ctrl + A``  and  ``"`` and select `second session`
    Ctrl + A and C (Will create a new tab, within screen session)
    Ctrl + A and K (will kill the session)
    Ctrl + A and space (next screen) # (or use the number)
    Ctrl + A and P (previous screen)
    Ctrl + A and " (list of screens)


Screen Help
-----

::

    screen --help
    Use: screen [-opts] [cmd [args]]
    or: screen -r [host.tty]

    Options:
    -4            Resolve hostnames only to IPv4 addresses.
    -6            Resolve hostnames only to IPv6 addresses.
    -a            Force all capabilities into each window's termcap.
    -A -[r|R]     Adapt all windows to the new display width & height.
    -c file       Read configuration file instead of '.screenrc'.
    -d (-r)       Detach the elsewhere running screen (and reattach here).
    -dmS name     Start as daemon: Screen session in detached mode.
    -D (-r)       Detach and logout remote (and reattach here).
    -D -RR        Do whatever is needed to get a screen session.
    -e xy         Change command characters.
    -f            Flow control on, -fn = off, -fa = auto.
    -h lines      Set the size of the scrollback history buffer.
    -i            Interrupt output sooner when flow control is on.
    -l            Login mode on (update /var/run/utmp), -ln = off.
    -ls [match]   or -list. Do nothing, just list our SockDir [on possible matches].
    -L            Turn on output logging.
    -m            ignore $STY variable, do create a new screen session.
    -O            Choose optimal output rather than exact vt100 emulation.
    -p window     Preselect the named window if it exists.
    -q            Quiet startup. Exits with non-zero return code if unsuccessful.
    -r [session]  Reattach to a detached screen process.
    -R            Reattach if possible, otherwise start a new session.
    -s shell      Shell to execute rather than $SHELL.
    -S sockname   Name this session <pid>.sockname instead of <pid>.<tty>.<host>.
    -t title      Set title. (window's name).
    -T term       Use term as $TERM for windows, rather than "screen".
    -U            Tell screen to use UTF-8 encoding.
    -v            Print "Screen version 4.01.00devel (GNU) 2-May-06".
    -wipe [match] Do nothing, just clean up SockDir [on possible matches].
    -x            Attach to a not detached screen. (Multi display mode).
    -X            Execute <cmd> as a screen command in the specified session.



Few other commands
-----

::


# apt-get install screen (On Debian based Systems)
# yum install screen (On RedHat based Systems)

Ctrl-A + ? # You will see all commands or parameters on screen.

To get out of the help screen, you can press “space-bar” button or “Enter“. 

screen -r # To re-attach the screen.
screen -ls # List screen session.
screen -r ScreenSessionName # To attach to a screen session.

ctrl-a + c # create a new screen (tab)
ctrl-a + p # move to previous tab
ctrl-a + n # move to next tab
ctrl-a + number # to select given tab.
ctrl-a + d # detach the screen


# For logging:
# Before you start the screen:
screen -L
# Within the screen session
ctrl-a + H # Note: caps H. To for logging whatever you do.



.. Note:: Please note that all shortcuts which use “Ctrl-A” is done without quotes).
