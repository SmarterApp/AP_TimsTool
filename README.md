# AP_TimsTool

Application providing a command line interface for managing items in TIMS.

## Summary

The tool has a set of commands it accepts.  The different commands require different options when executing them.  For example, some commands require an input file be provided.

## Installation

TODO - finish this section.
Currently the project must first be built. 

- Clone the project locally.  
- Using a terminal, navigate into the root of the project.
- Build the project ./gw bootRePack
- Run `./tims` followed by whatever commands you wish to execute.

NOTE: To run locally against an external environment, the main tool property to override is `tims.tool.apiGatewayUrl`. The environment variable to use is `TIMS_TOOL_API_GATEWAY_URL` .

Set this prior to running the tool. Ex: ```$ export TIMS_TOOL_API_GATEWAY_URL=https://iat-api-gateway-awsdev.sbtds.org```

## Options

These are the most basic options when first getting started

- `-h`: prints the help message
- `-c`: lists the tool commands 

### Commands
Command: `create-test-package` 
Description: Creates an XML test package based on the input spreadsheet

- `-i`: spreadsheet name
- `-o`: file name to write results

Example usage and output from create-test-package:
```
$ ./tims create-test-package -i SBAC-IAB-FIXED-G11M-Winter-2017-2018.xlsx -o outputFile.xml
starting...

validated..., submitting request to TIMS
The results have been written to outputFile.xml

complete
$
```

Command: `create-saaif-content-package`
Description: Initiates an SAAIF content package job
- `-d`: the item id(s) to create SAAIF item packages for, as a comma delimited list with no spaces
Usage: `create-saaif-content-package -d 1234,5678`
Example usage and output from create-saaif-content-package:
```
$ ./tims create-saaif-content-package -d 209572,209783,209895
starting...

validated..., submitting request to TIMS translation service
The content package creation request was successful:
Content Package Id: 1
Item Ids: [209572, 209783, 209895]

complete

Process finished with exit code 0

```

Command: `get-saaif-content-package-status`
Description: Gets the status of an SAAIF content package job 
Example usage and output from get-saaif-content-package-status:
```
$ ./tims get-saaif-content-package-status 1
starting...

validated..., submitting request to TIMS translation service
Content Package Status for id 1: COMPLETED

complete

Process finished with exit code 0

```

Command: `get-saaif-content-package-archive`
Description: Gets the status of an SAAIF content package job 
Usage: `get-saaif-content-package-status -1`

Command: `get-saaif-content-package-archive`
- The content package id
- `-o`: file name to write the archive package
Example usage and output from get-saaif-content-package-status:
```
$ ./tims get-saaif-content-package-archive -o package-1.zip 1
starting...

validated..., submitting request to TIMS translation service
The results have been written to package-1.zip

complete

Process finished with exit code 0


```



## Authorization

At this time, the user is required to obtain an auth token first. 

*This will be changed so the user can either login via the tims-tool, or the user could have credentials in the environment and the tims-tool uses those to get the auth-token.*

