---
title: "Implementing a plugin architecture in C"
date: 2017-11-13T15:29:17+05:30
tags:
- C
- how-to
categories:
- project
---

Recently I was working on [a
project](https://github.com/coditva/Synergy-linux) where I had decided to
make the application extensible by use of plugins (or add-ons). A plugin is a
piece of code which is not part of the core app and is not required for proper
working of it; it provides with additional functionality and allows third-party
developers to extend the app.

The developer who makes the plugin infrastructure is required to provide a way
to:

- Look for plugins
- Load them
- Run them at appropriate time

One way to implement a plugin system in a pre-compiled language like C is by
the use of a [shared object]
(https://en.wikipedia.org/wiki/Library_\(computing\)#Shared_libraries)
(or shared library). A dynamically linked shared object (also called a DSO) can
be written and compiled independent of the core application and the binary thus
produced can be placed in a pre-decided folder (like `/plugins`) where the core
app can discover and load it.


#### Loading plugins

The app looks for plugins in a specific location (say `/plugins`) and tries to load the initialization function for each plugin. We have keep a pre-defined format to denote the initialization function for each plugin such as:
```c
void plugin_PLUGIN_NAME_init(info_t *info);
/* this is just one way to declare an init function. */
```

`info_t` can be defined however you like. For this example I'm gonna define it as:
```c
/* a struct to store the info to be passed to the plugin */
typedef struct {
    int some_info;
} into_t;
```

The core app loads the plugin with the `dlopen` function declared in the `<dlfcn.h>` header. `dlopen` function is used in the core app as:
```c
void *handle;
char plugin_path[] = "./plugins/myplugin.so";

handle = dlopen(plugin_path, RTLD_NOW);
/* check man(3) dlopen for more info on this */

if (!handle) {
    /* error */
}
```

This returns a 'handle' for the object which is used with other functions to operate on the shared object.

The initialization function of the plugin can be executed as:
```c
/* define the init function pointer type */
typedef void (*plugin_init_func_t)(info_t *);

char function_name[] = "plugin_myplugin_init";
plugin_init_func_t plugin_init_func;

/* get the address of the init function */
plugin_init_func = (plugin_init_func_t) (__intptr_t)
    dlsym(handle, function_name);

if (plugin_init_func == NULL) {
    /* error */
}

/* run the function */
(*plugin_init_func)(info);
```

**Important note**: The core app must be compiled with the linker flag `-ldl`


### Writing plugins

The plugins must have the initialization function as mentioned before. These function can be used to attach handler functions for events or hooks. The events must be defined by the core app and the ability to attach handlers must be provided to the plugins as part of the plugins development API.

```c
/* an arbitrary event handler
 * it is generally a good idea to append the function name with the plugin
 * name to avoid conflict */
void myplugin_some_handler(info_t *info)
{
    /* do whatever you intend to */
}

/* the init function */
void plugin_myplugin_init(info_t *info)
{
    /* play with info passed */
    info -> some_info += 20;

    /* attach handlers to events */
    event_attach(EVENT_NAME, myplugin_some_handler);
}
```

**Important note**: The plugins must be compiled with the compile-time flag `-fpic` and the linker flag `-shared`

You can find my implementation of events and plugins in [this project](https://github.com/coditva/Synergy-linux).
