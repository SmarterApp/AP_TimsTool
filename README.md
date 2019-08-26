# AP_TimsTool

Application providing a command line interface for managing items in TIMS.

## Installation

TODO

## Summary

The tool has a set of commands it accepts.  The different commands require different options when executing them.  For example, some commands require an input file be provided.

## Options

These are the most basic options when first getting started

- -h : Prints the help message
- -c : Lists the tool commands 

A new command has been added to the tool.  The command is ‘create-test-package’.  It requires three command line options

- -i <spreadsheet name>
- -o <file name to write results>
- -t <authorization token>

## Authorization

At this time, the user is required to obtain an auth token first. 

*This will be changed so the user can either login via the tims-tool, or the user could have credentials in the environment and the tims-tool uses those to get the auth-token.*

