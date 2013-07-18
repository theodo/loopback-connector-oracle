## Loopback Oracle Connector

Connect Loopback to Oracle

## Installation

You need to download and install Oracle instant client from following links:

http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html

1. Instant Client Package - Basic: All files required to run OCI, OCCI, and JDBC-OCI applications
2. Instant Client Package - SDK: Additional header files and an example makefile for developing Oracle applications with Instant Client

For Windows, please make sure 12_1 version is used.

<ul>
<li>Please make sure you download the correct packages for your system architecture, such as 64 bit vs 32 bit
<li>Unzip the files 1 and 2 into the same directory, such as /opt/instantclient_11_2 or c:\instantclient_12_1
</ul>


On MacOS or Linux:

1. Set up the following environment variables

MacOS/Linux:

    export OCI_HOME=<directory of Oracle instant client>
    export OCI_LIB_DIR=$OCI_HOME
    export OCI_INCLUDE_DIR=$OCI_HOME/sdk/include

2. Create the following symbolic links

MacOS:

    cd $OCI_LIB_DIR
    ln -s libclntsh.dylib.11.1 libclntsh.dylib
    ln -s libocci.dylib.11.1 libocci.dylib

Linux:

    cd $OCI_LIB_DIR
    ln -s libclntsh.so.11.1 libclntsh.so 
    ln -s libocci.so.11.1 libocci.so 

3. Configure the dynamic library path

MacOS:

    export DYLD_LIBRARY_PATH=$OCI_LIB_DIR

On Windows, you need to set the environment variables:

If you have VisualStudio 2012 installed,

    OCI_INCLUDE_DIR=C:\instantclient_12_1\sdk\include
    OCI_LIB_DIR=C:\instantclient_12_1\sdk\lib\msvc\vc11
    Path=...;c:\instantclient_12_1\vc11;c:\instantclient_12_1

**Please make sure c:\instantclient_12_1\vc11 comes before c:\instantclient_12_1**

If you have VisualStudio 2010 installed,

    OCI_INCLUDE_DIR=C:\instantclient_12_1\sdk\include
    OCI_LIB_DIR=C:\instantclient_12_1\sdk\lib\msvc\vc10
    Path=...;c:\instantclient_12_1\vc10;c:\instantclient_12_1

**Please make sure c:\instantclient_12_1\vc10 comes before c:\instantclient_12_1**

## Discovering Models

Oracle data sources allow you to discover model definition information from existing oracle databases. See the following APIs:

 - [dataSource.discoverModelDefinitions([username], fn)](https://github.com/strongloop/loopback#datasourcediscovermodeldefinitionsusername-fn)
 - [dataSource.discoverSchema([owner], name, fn)](https://github.com/strongloop/loopback#datasourcediscoverschemaowner-name-fn)

**Type Mapping** TODO

 - Number
 - Boolean
 - String
 - null
 - Object
 - undefined
 - Date
 - Array
 - Buffer

## Destroying Models

Destroying models may result in errors due to foreign key integrity. Make sure to delete any related models first before calling delete on model's with relationships.

## Auto Migrate / Auto Update

After making changes to your model properties you must call `Model.automigrate()` or `Model.autoupdate()`. Only call `Model.autoupdate()` on new models.

## Type Mapping

- 



## Running tests

    npm test