---
title: NeRu Debugging
description: This documentation describes NeRu Debugging
meta_title: NeRu Debugging
---

# NeRu Debugging

NeRu allows you to debug your code locally on your machine as if it was deployed on the NeRu platform. It works by starting a remote debug server that proxies requests to your machine. Since is it local debugging, you can use your IDE to attach a debugger, set breakpoints and run through the execution of your project line by line. 

## Debugger Dependencies

* Node.JS: You will need to install [`nodemon`](https://www.npmjs.com/package/nodemon) globally:

    ```sh
    npm install -g nodemon
    ```

## Start a Debug Session

Run the debug start command from in terminal session in your project directory. Note that the first time you run this it will set up and install a few more things:

```sh
neru debug 
```

You can also start a named debugger, which allows you to keep the same URL between debugging sessions:

```sh
neru debug --name <name>
```

Named debuggers can also be specified in your configuration file (`neru.yml`) by adding a `debug` object at the root level:

```yaml
project:
    name: project
debug:
    name: debugger
```


This will start the server, once done you can start using your application. The debugger will will show any incoming and outgoing requests. Code changes you make and save will trigger the debugger to reload automatically.

## Debug from VSCode

Using VSCode you can attach a debugger to the server to allow you to set breakpoints and step through your code. To do so click on the *Run and Debug* button, then *create a `launch.json` file*. Select `nodejs` as a preset: 

![Run and Debug in VSCode](/images/neru/neru-vscode-debug.png)

In the `launch.json` file replace the entire contents of the file with the following:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "attach",
            "name": "Attach Neru Debugger",
            "port": 9229,
            "restart": true,
            "localRoot": "${workspaceFolder}",
        }
    ]
}
```

This will configure the VSCode debugger to work with the NeRu debug server. The debug server is running on port 9229, so if you are using a different program to debug, attach to this port. Start your debug server if you have not already with `neru debug`, then click on the *start debugging* button to attach the VSCode debugger:

![Start debugging button in VSCode](/images/neru/neru-vscode-attach.png)

Once attached you will have access to the debug controls.

### Breakpoints

By clicking to the left of a line number you can set a breakpoint in your code, so the program will pause on this line and allow you inspect the program, step over and so on:

![Setting a breakpoint in VSCode](/images/neru/neru-vscode-breakpoint.png)

When your breakpoint is hit, VSCode will highlight the line that it has stopped on, and using the debug console you can print out values from your program: 

![Using the debug console in VSCode](/images/neru/neru-vscode-active-breakpoint.png)

Or you can use the debug controls to inspect your even deeper by stepping in and out of functions, or continuing past the current line.
