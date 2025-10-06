si4735 is a library for the [iota](https://github.com/blanu/iota) programming language

si4735-arduino is an Arduino library providing iota bindings to the [pu2clr/SI4735](https://github.com/pu2clr/SI4735) C++ library. The pu2clr/SI4735 C++ library provides a driver for the [SI473X](https://d1ehax0mqsd4rz.cloudfront.net/-/media/SkyWorks/SL/documents/public/data-shorts/Si4734-35-short.pdf?rev=1c51b50cea7a4467beab2706e7c38979) family of devices.

The SI473X family of devices allow for the reception of radio signals such as AM, FM, SW, and LW. 

To use the si4735-arduino library you will need one of these devices, an Arduino of some sort, and an interest in the iota programming language.

This library is just a wrapper for the C++ library. For most questions you should consult its documentation or the datasheet for your specific device.

The main advantage of using the iota bindings instead of the C++ library is that iota is interpreted and dynamically typed.
This allows you to explore the library interactively instead of writing Arduino sketches all at once. iota also features
a cross-platform data transport protocol called ion. ion includes remote procedure calls, so with proper support for your platform
you could potentially drive the radio receiver chip from another device besides the Arduino.
