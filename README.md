# GLFW

## Introduction

GLFW is a free, Open Source, multi-platform library for OpenGL and OpenGL ES
application development.  It provides a simple, platform-independent API for
creating windows and contexts, reading input, handling events, etc.

Version 3.1 is *not yet described*.

If you are new to GLFW, you may find the
[introductory tutorial](http://www.glfw.org/docs/latest/quick.html) for GLFW
3 useful.  If you have used GLFW 2 in the past, there is a
[transition guide](http://www.glfw.org/docs/latest/moving.html) for moving to
the GLFW 3 API.

Note that a number of source files have been added or renamed in 3.1, which may
require you to update any custom build files you have.


## Compiling GLFW

See the [Compiling GLFW](http://www.glfw.org/docs/latest/compile.html) guide in
the GLFW documentation.


## Using GLFW

See the
[Building programs that use GLFW](http://www.glfw.org/docs/latest/build.html)
guide in the GLFW documentation.


## Reporting bugs

Bugs are reported to our [issue tracker](https://github.com/glfw/glfw/issues).
Please always include the name and version of the OS where the bug occurs and
the version of GLFW used.  If you have cloned it, include the commit ID used.

If it's a build issue, please also include the build log and the name and
version of your development environment.

If it's a context creation issue, please also include the make and model of your
graphics card and the version of your driver.

This will help both us and other people experiencing the same bug.


## Dependencies

GLFW bundles a number of dependencies in the `deps/` directory.

 - [Khronos extension headers](https://www.opengl.org/registry/) for API
   extension symbols used by GLFW
 - [getopt\_port](https://github.com/kimgr/getopt_port/) for examples
   with command-line options
 - [TinyCThread](https://github.com/tinycthread/tinycthread) for threaded
   examples
 - An OpenGL 3.2 core loader generated by
   [glad](https://github.com/Dav1dde/glad) for examples using modern OpenGL


## Changelog

 - Added `GLFWcursor` custom system cursor handle
 - Added `glfwCreateCursor`, `glfwCreateStandardCursor`, `glfwDestroyCursor` and
   `glfwSetCursor` for managing system cursor images
 - Added `GLFWimage` struct for passing 32-bit RGBA images
 - Added monitor and adapter identifier access to native API
 - Added `glfwSetDropCallback` and `GLFWdropfun` for receiving dropped files
 - Added `glfwPostEmptyEvent` for allowing secondary threads to cause
   `glfwWaitEvents` to return
 - Added `empty` test program for verifying posting of empty events
 - Added `glfwSetCharModsCallback` for receiving character events with modifiers
 - Added `glfwGetWindowFrameSize` for retrieving the size of the frame around
   the client area of a window
 - Added `GLFW_AUTO_ICONIFY` for controlling whether full screen windows
   automatically iconify (and restore the previous video mode) on focus loss
 - Added `GLFW_DONT_CARE` for indicating that any value is acceptable
 - Added `GLFW_DOUBLEBUFFER` for controlling whether to use double buffering
 - Added `GLFW_CONTEXT_RELEASE_BEHAVIOR` and values
   `GLFW_ANY_RELEASE_BEHAVIOR`, `GLFW_RELEASE_BEHAVIOR_FLUSH` and
   `GLFW_RELEASE_BEHAVIOR_NONE` for `GL_KHR_context_flush_control` support
 - Added `GLFW_INCLUDE_ES31` for including the OpenGL ES 3.1 header
 - Added `GLFW_FLOATING` for creating always-on-top windowed mode windows
 - Added `GLFW_FOCUSED` window hint for controlling initial input focus
 - Added *partial and experimental* support for Wayland
 - Added *partial and experimental* support for Mir
 - Changed the default of `GLFW_REFRESH_RATE` to `GLFW_DONT_CARE` to maintain
   the default behavior
 - Changed static library to build as position independent code for easier use
   from the Rust language
 - Bugfix: The debug context attribute was set from `GL_ARB_debug_output` even
           when a debug context had not been requested
 - Bugfix: The particles example was not linked against the threading library
 - Bugfix: The cursor was not positioned over newly created full screen windows
 - [Cocoa] Added `_GLFW_USE_RETINA` to control whether windows will use the full
           resolution on Retina displays
 - [Cocoa] Bugfix: Using a 1x1 cursor for hidden mode caused some screen
                   recorders to fail
 - [Cocoa] Bugfix: Some Core Foundation objects were leaked during joystick
                   enumeration and termination
 - [Cocoa] Bugfix: One copy of each display name string was leaked
 - [Cocoa] Bugfix: Monitor enumeration caused a segfault if no `NSScreen` was
                   found for a given `CGDisplay`
 - [Cocoa] Bugfix: Modifier key events were lost if the corresponding modifier
                   bit field was unchanged
 - [Cocoa] Bugfix: Joystick enumeration took hundreds of ms on some systems
 - [Cocoa] Bugfix: The cursor was hidden when the user resized a GLFW window
 - [Win32] Enabled generation of pkg-config file for MinGW
 - [Win32] Removed option to require explicitly linking against `winmm.dll`
 - [Win32] Bugfix: Failure to load winmm or its functions was not reported to
                   the error callback
 - [Win32] Bugfix: Some keys were reported based on the current layout instead
                   of their physical location
 - [Win32] Bugfix: Maximized hidden windows were restored by `glfwShowWindow`
 - [Win32] Bugfix: Context re-creation was not triggered by sRGB hint
 - [Win32] Bugfix: Full screen windows were incorrectly sized and placed on some
                   systems
 - [Win32] Bugfix: Gamma ramp functions acted on entire desktop instead of the
                   specified monitor
 - [Win32] Bugfix: The wrong incorrect physical size was returned for
                   non-primary monitors
 - [Win32] Bugfix: X-axis scroll offsets were inverted
 - [Win32] Bugfix: The Optimus HPG forcing variable was not correctly exported
 - [X11] Added run-time support for systems lacking the XKB extension
 - [X11] Made GLX 1.3 the minimum supported version
 - [X11] Replaced `XRRGetScreenResources` with `XRRGetScreenResourcesCurrent`
         for monitor property retrieval
 - [X11] Bugfix: The case of finding no usable CRTCs was not detected
 - [X11] Bugfix: Detection of broken Nvidia RandR gamma support did not verify
                 that at least one CRTC was present
 - [X11] Bugfix: A stale `_NET_SUPPORTING_WM_CHECK` root window property would
                 cause an uncaught `BadWindow` error
 - [X11] Bugfix: No check was made for the presence of GLX 1.3 when
                 `GLX_SGIX_fbconfig` was unavailable
 - [X11] Bugfix: The message type of ICCCM protocol events was not checked
 - [X11] Bugfix: `glfwDestroyWindow` did not flush the output buffer
 - [X11] Bugfix: Window frame interactions were reported as focus events
 - [X11] Bugfix: Workaround for legacy Compiz caused flickering during resize
 - [X11] Bugfix: The name pointer of joysticks were not cleared on disconnection
 - [X11] Bugfix: Video mode dimensions were not rotated to match the CRTC
 - [X11] Bugfix: Unicode character input ignored dead keys
 - [X11] Bugfix: X-axis scroll offsets were inverted
 - [X11] Bugfix: Full screen override redirect windows were not always
                 positioned over the specified monitor


## Contact

The official website for GLFW is [glfw.org](http://www.glfw.org/).  There you
can find the latest version of GLFW, as well as news, documentation and other
information about the project.

If you have questions related to the use of GLFW, we have a
[support forum](https://sourceforge.net/p/glfw/discussion/247562/), and the IRC
channel `#glfw` on [Freenode](http://freenode.net/).

If you have a bug to report, a patch to submit or a feature you'd like to
request, please file it in the
[issue tracker](https://github.com/glfw/glfw/issues) on GitHub.

Finally, if you're interested in helping out with the development of GLFW or
porting it to your favorite platform, we have an occasionally active
[developer's mailing list](https://lists.stacken.kth.se/mailman/listinfo/glfw-dev),
or you could join us on `#glfw`.


## Acknowledgements

GLFW exists because people around the world donated their time and lent their
skills.

 - Bobyshev Alexander
 - artblanc
 - arturo
 - Matt Arsenault
 - Keith Bauer
 - John Bartholomew
 - Niklas Behrens
 - Niklas Bergström
 - Doug Binks
 - blanco
 - Martin Capitanio
 - Lambert Clara
 - Andrew Corrigan
 - Noel Cower
 - Jarrod Davis
 - Olivier Delannoy
 - Paul R. Deppe
 - Michael Dickens
 - Jonathan Dummer
 - Ralph Eastwood
 - Michael Fogleman
 - Gerald Franz
 - GeO4d
 - Marcus Geelnard
 - Eloi Marín Gratacós
 - Stefan Gustavson
 - Sylvain Hellegouarch
 - Matthew Henry
 - heromyth
 - Lucas Hinderberger
 - Paul Holden
 - Toni Jovanoski
 - Arseny Kapoulkine
 - Osman Keskin
 - Cameron King
 - Peter Knut
 - Quinten Lansu
 - Robin Leffmann
 - Glenn Lewis
 - Shane Liesegang
 - Дмитри Малышев
 - Martins Mozeiko
 - Tristam MacDonald
 - Hans Mackowiak
 - Kyle McDonald
 - David Medlock
 - Jonathan Mercier
 - Marcel Metz
 - Kenneth Miller
 - Bruce Mitchener
 - Jack Moffitt
 - Jeff Molofee
 - Jon Morton
 - Pierre Moulon
 - Julian Møller
 - Kamil Nowakowski
 - Ozzy
 - Andri Pálsson
 - Peoro
 - Braden Pellett
 - Arturo J. Pérez
 - Cyril Pichard
 - Pieroman
 - Jorge Rodriguez
 - Ed Ropple
 - Riku Salminen
 - Brandon Schaefer
 - Sebastian Schuberth
 - Matt Sealey
 - SephiRok
 - Steve Sexton
 - Systemcluster
 - Dmitri Shuralyov
 - Daniel Skorupski
 - Bradley Smith
 - Julian Squires
 - Johannes Stein
 - Justin Stoecker
 - Nathan Sweet
 - TTK-Bandit
 - Sergey Tikhomirov
 - Samuli Tuomola
 - urraka
 - Jari Vetoniemi
 - Ricardo Vieira
 - Simon Voordouw
 - Torsten Walluhn
 - Patrick Walton
 - Jay Weisskopf
 - Frank Wille
 - yuriks
 - Santi Zupancic
 - Jonas Ådahl
 - Lasse Öörni
 - All the unmentioned and anonymous contributors in the GLFW community, for bug
   reports, patches, feedback, testing and encouragement

