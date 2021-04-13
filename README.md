AUTHOR - Raman Sailopal

BACKGROUND - 

This Linux command line utility allows you to write Intersystems objectscript code outside of an IRIS environment, i.e. using vi and then execute it from the command line in much the same was as you do with awk

PROCESS - 

A temporary flat file is created with all the relevant Intersystems routine import headings followed by the code from the passed file. This is then imported into IRIS, run, and then deleted, before finally removing the raw flat file

PREREQUISITES - 

It is assumed that a working version of Intersystems IRIS is installed as as well as iriscmd (attained from here - https://github.com/RamSailopal/iriscmd

PARAMETERS -

           First - The name of the raw code file
           Second (optional) - The IRIS instance name.
           If this is not set the environmental variable IRISINST will be checked

EXAMPLE USAGE - 

Example 1:

           cat testrout.ro
            S TESTVAR="hello;there;how;are;you"
            W $P(TESTVAR,";",4)

           iriscode testrout.ro "IRIS"
           are

Example 2:
        
            export IRISINST="IRIS"
            cat testrout.ro
            #!/usr/local/bin/iriscode
             S TESTVAR="hello;there;how;are;you"
             W $P(TESTVAR,";",4)

            chmod o+x testrout.ro
            ./testrout.ro
            are

INSTALLATION -

            git clone https://github.com/RamSailopal/iriscode.git
            cp iriscode/iriscode /usr/local/bin
