<img src="./images/logo.png" width="150px"/>
<span style="font-size:40px;padding-left:100px">Cisco Intersight</span>

<img src="./images/intersight.png" style="padding-top:100px"/>
<img src="./images/golang.png" style="padding-top:100px;padding-left:150px" width="400px"/>

# Cisco Intersight

# Overview
Python is a great and very popular scripting language, especially amongst the growing DevOps teams.  It is therefore very common to find many SDK's developed in Python, however, it is also common to find these teams using other languages, such as Go.

In this initial tutorial, we will go through the process step by step of reverse engineering the Cisco Intersight Python SDK into a Go version.

In future tutorials we will extend this functionality and make some real life customer API to short cut common requirements and produce a Web frontend / dashboard to display our API information.

# Tools
To run through this tutorial we will use a number of tools to achieve our goal, many of the screenshots and tools will reference a Mac, however, the steps, tools and goals can all be achieved on Windows and Linux too.

We will need;

-	**Golang** - Any version should support what we are doing, however, you should always try to run the most recent version if possible.  As of writing this Go is version 1.12.5.
-	**Visual Studio Code** - This is my preferred IDE, however, there are no specific tools that we will use that are unique to VSCode.  If you prefer Sublime, IntelliJ, TextEdit, they will all work fine, however the screenshots in this tutorial will not match.  As of writing VSCode is version 1.35.0.
-	**Internet Connection** - The Github repository, but more so Intersight itself is a SaaS tool and so having an active and reliable internet connection is required.
-	**A terminal** - Any terminal or command prompt should suffice.  This will be used for executing our application at multiple stages and for displaying the output.  I will be using iTerm, however, the standard terminal or command prompt would be fine.  As of writing this iTerm is version 3.3.0

# Starting Point
There are many places to start our journey, we could jump into the code, we could step through installing the tools, storyboarding, and many other steps.  However, the best place to start is to review some working code that has been written and tested and will be what we reverse engineer into Go code.

At this pointing understanding the ins and outs of the Python script is not required.  If you do have some background in Python that will be advantageous, but not a necessity.

We will start by looking here, this is the main repository for the REST interface;
[Cisco UCS Intersight Rest repository](https://github.com/CiscoUcs/intersight-rest)

We can then explore the specific repository for the Python code;
[Cisco UCS Intersight Python main page](https://github.com/CiscoUcs/intersight-rest/tree/master/python)

And finally we can look at the piece of Python code we will reverse engineer;
[Cisco UCS Intersight Python code](https://github.com/CiscoUcs/intersight-rest/blob/master/python/intersight_rest/intersight_rest.py)

Spend some time looking at the code and understanding the different functions (in Python these start with the word *def*).  The real function, the one that brings all of the different functions together and the one that actually does the API call is the function *def intersight_call*.  Have a look at this function and the flow.

We will spend more time on the specifics, however for now, anything that is not clear or any new Python command, have a quick look online to understand what it is actually doing.