# AP_TimsTool

Application providing a command line interface for managing items in TIMS.

## Summary

The tool has a set of commands it accepts.  The different commands require different options when executing them.  For example, some commands require an input file be provided.

## Installation

Go to the released version you want to install.  This is on the [releases page](https://github.com/SmarterApp/AP_TimsTool/releases).  The current released version is 1.0.1.

- Download the JAR file to whichever directory you want
- Run `java -jar <jar_name>` followed by whatever commands you wish to execute.

NOTE: To run locally against an external environment, the main tool property to override is `tims.tool.apiGatewayUrl`. The environment variable to use is `TIMS_TOOL_API_GATEWAY_URL` .

### Environment Variables

The following SSO-related environment variables need to be defined before running the application:

<pre>
# The URL to the TIMS Gateway that is used to make OAuth2 calls to TIMS
export TIMS_TOOL_API_GATEWAY_URL=
# These are OpenAM credentails that will need to be provided for the TIMS environment
export TIMS_TOOL_SSO_GRANT_TYPE=
export TIMS_TOOL_SSO_PASSWORD=
export TIMS_TOOL_SSO_CLIENT_ID=

# The TIMS User ID to be used for authentication
export TIMS_TOOL_SSO_USERNAME=
# The TIMS password to be used for authentication
export TIMS_TOOL_SSO_CLIENT_SECRET=

# The URL to the OAUTH2 endpoint for OpenAM
export TIMS_TOOL_SSO_URL=
</pre>

When setting up the tool for the first time please reach out to the IT team to provide you with the proper information.

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

<pre>
$ java -jar <jar-name>  create-test-package -i SBAC-IAB-FIXED-G11M-Winter-2017-2018.xlsx -o outputFile.xml
starting...

validated..., submitting request to TIMS
The results have been written to outputFile.xml

complete
</pre>

Command: `create-saaif-content-package`
Description: Initiates an SAAIF content package job
- `-d`: the item id(s) to create SAAIF item packages for, as a comma delimited list with no spaces
Usage: `create-saaif-content-package -d 1234,5678`
Example usage and output from create-saaif-content-package:

<pre>
$ java -jar <jar-name> create-saaif-content-package -d 209572,209783,209895
starting...

validated..., submitting request to TIMS translation service
The content package creation request was successful:
Content Package Id: 1
Item Ids: [209572, 209783, 209895]

complete

Process finished with exit code 0

</pre>

Command: `get-saaif-content-package-status`
Description: Gets the status of an SAAIF content package job 
Example usage and output from get-saaif-content-package-status:

<pre>
$ java -jar <jar-name> get-saaif-content-package-status 1
starting...

validated..., submitting request to TIMS translation service
Content Package Status for id 1: COMPLETED

complete

Process finished with exit code 0
</pre>

Command: `get-saaif-content-package-archive`
Description: Gets the status of an SAAIF content package job 
Usage: `get-saaif-content-package-status -1`

Command: `get-saaif-content-package-archive`
- The content package id
- `-o`: file name to write the archive package
Example usage and output from get-saaif-content-package-status:

<pre>
$ java -jar <jar-name> get-saaif-content-package-archive -o package-1.zip 1
starting...

validated..., submitting request to TIMS translation service
The results have been written to package-1.zip

complete

Process finished with exit code 0
<pre>
