# Installation

Install dependencies.

    sudo apt-get update
    sudo apt-get install faketime
   
Copy timeprivacy to /usr/local/bin/.

    sudo cp timeprivacy /usr/local/bin/
   
# Demonstration
Create a file /usr/local/bin/tpdate.

    #!/bin/bash
    faketime "$(timeprivacy date)" date

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
    faketime "$(timeprivacy $prog)" $prog $*

