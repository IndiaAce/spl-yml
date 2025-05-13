# spl-yml
A simple web app that takes your SPL and creates detection CI/CD ready yml files. It's lovely.

Given a detection name, description, and SPL search string, output a correctly indented suppression YAML snippet ready to paste into your CI/CD pipeline

Ultimately this just needs a simple GUI:
    1. Enter Detection Name
    2. Enter Detection Description
    3. Enter Detection SPL

Script will then automatically convert this input into a yml CI/CD-ready detection. (v.2 could be plugging that into GPT API that fleshes that out a bit more)

Expected input:
    1. Cobaltstrike Named Pipe
    2. This analytic detects the execution of cobaltstrike named pipe execution
    3. | tstats summariesonly=t fillnull value="unknown" values(Files.file_name) as file_name values(Files.command_line) as command_line WHERE Files.properties IN ("cobaltstrike", "named pipe")

Expected output YML:
id: lw-cobaltstrike_named_pipe
description: | 
    This analytic detects the execution of cobaltstrike named pipe execution
content: |
    | tstats summariesonly=t fillnull value="unknown" values(Files.file_name) as file_name values(Files.command_line) as            command_line WHERE Files.properties IN ("cobaltstrike", "named pipe")