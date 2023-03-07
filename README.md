# setup-SHFB

This is a Github action to install EWSoftware/SHFB for later use.

## Example

    name: "Test"

    on: [push, pull_request]

    jobs:
      build:
        runs-on: windows-2022
    
        steps:
        - name: Install checkout
          uses: actions/checkout@v3
      
        - name: Add msbuild to PATH
          uses: microsoft/setup-msbuild@v1.1
      
        - name: Install SHFB
          uses: Bassman2/setup-SHFB@v1
          with:
            version: 2023.3.4.0
        
        - name: Create Test Documentation
          run: msbuild setup-SHFB-Test.sln /p:configuration="Release" /m /verbosity:minimal

## SHFB Versions

The version parameter is optional. If no version is set the latest version will be used.

Currently the following versions can be used:

* 2023.3.4.0  (default)
* 2022.12.30.0
* 2022.10.15.0
* 2022.8.14.1

## Runner

This action can be used for the windows-latest or windows-2022 and windows-2019 runners.