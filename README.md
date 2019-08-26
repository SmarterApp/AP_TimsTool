# AP_TimsTool

Application providing a command line interface for managing items in TIMS.

## Summary

The tool has a set of commands it accepts.  The different commands require different options when executing them.  For example, some commands require an input file be provided.

## Installation

TODO - finish this section
Currently the project must first be built. 

- Clone the project locally.  
- Using a terminal, navigate into the root of the project.
- Build the project ./gw bootRePack
- Run `./tims` followed by whatever commands you wish to execute.

NOTE: To run locally against an external environment, the main tool property to override is `tims.tool.apiGatewayUrl`. The environment variable to use is `TIMS_TOOL_API_GATEWAY_URL.`

Set this prior to running the tool. Ex: ```$ export TIMS_TOOL_API_GATEWAY_URL=https://iat-api-gateway-awsdev.sbtds.org```

## Options

These are the most basic options when first getting started

- `-h`: prints the help message
- `-c`: lists the tool commands 

A new command has been added to the tool.  The command is ‘create-test-package’.  It requires three command line options

- `-i`: spreadsheet name
- `-o`: file name to write results
- `-t`: authorization token
  
Example usage and output from create-test-package:
```
$ ./tims create-test-package -t 12345-1234-1234-1234-123456789 -i SBAC-IAB-FIXED-G11M-Winter-2017-2018.xlsx -o outputFile.xml
starting...

validated..., submitting request to TIMS
The results have been written to outputFile2.xml

complete
$
```

## Authorization

At this time, the user is required to obtain an auth token first. 

*This will be changed so the user can either login via the tims-tool, or the user could have credentials in the environment and the tims-tool uses those to get the auth-token.*

