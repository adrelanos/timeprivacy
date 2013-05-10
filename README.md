# MERGED
This script has been [merged](https://github.com/wolfcw/libfaketime/pull/16#issuecomment-17706741) into [libfaketime](https://github.com/wolfcw/libfaketime) ([src](https://github.com/wolfcw/libfaketime/blob/master/src/timeprivacy)).

You can leave feedback and/or contribiute here or to [libfaketime](https://github.com/wolfcw/libfaketime/issues) and mention @adrelanos as far as timeprivacy is concerned.

# Installation

Install dependencies.

    sudo apt-get update
    sudo apt-get install faketime
   
Copy timeprivacy to /usr/local/bin/.

    sudo cp timeprivacy /usr/local/bin/
   
# Demonstration
Create a file /usr/local/bin/tpdate.

    #!/bin/bash
    faketime "$(timeprivacy)" date $*

Try.   
   
    ~ $ tpdate
    Fri May  3 00:00:01 UTC 2013
    ~ $ tpdate
    Fri May  3 00:00:02 UTC 2013
    ~ $ tpdate
    Fri May  3 00:00:03 UTC 2013
    ~ $ tpdate
    Fri May  3 00:00:04 UTC 2013
    ~ $ tpdate
    Fri May  3 00:00:05 UTC 2013

Let's try something more interesting. Let's add timeprivacy to git. We need to create a wrapper.
It will take precedence over /usr/bin/git, thus run faketime and timeprivacy before git itself.
Create a file /usr/local/bin/git.
   
    #!/bin/bash
    prog=git
    faketime "$(timeprivacy)" $prog $*

# More Features
Usage.

    timeprivacy [-h help] [-d day] [-m month] [-y year] [-i increment in seconds (0-60)] [-r random increment in seconds (0-60)] [-f history folder]

Example #1.

    timeprivacy -d 30 -m 12 -y 2013 -i 10 -f /tmp/$SCRIPTNAMEtest
    
Example #2.

    sudo $SCRIPTNAME -d 30 -m 12 -y 2013 -r -f /tmp/$SCRIPTNAMEtest
