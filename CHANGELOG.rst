^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package serial
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

2.0.1 (2025-01-09)
------------------
* Add cmake flags and use target include
* Contributors: Luis Camero

2.0.0 (2023-07-25)
------------------
* Revert "Merge branch 'ament_cmake'"
  This reverts commit 8e0effcd36b855701d9327aecff949d7f2b20e31.
* Revert "Remove test that breaks the build"
  This reverts commit 7fe3be8d5f24db9837fff7e5b2fc45dcb464eef0.
* Remove test that breaks the build
* Convert package to ament_cmake
* Fix the build and cleanup CMakeLists
* Add setupapi to ament_export_libraries
  This prevents dependent libraries from failing with something like: serial.lib(list_ports_win.obj) : error LNK2019: unresolved external symbol __imp_SetupDiEnumDeviceInfo referenced in
* Migrated to ROS2
  Followed migration instructions in https://index.ros.org/doc/ros2/Contributing/Migration-Guide/
* Fix memory leak when exception is thrown by impl classes in (`#198 <https://github.com/clearpathrobotics/serial-ros2/issues/198>`_)
  Serial::read() vector and string variants.
* whitespace
* whitespace
* reduce the number of jobs on travis (`#172 <https://github.com/clearpathrobotics/serial-ros2/issues/172>`_)
  * reduce the number of jobs on travis
  * update usage of pip due to changes in Homebrew
  * update pip and ensure the right one is being used with an alias
  * force reinstall pip to get `pip` on PATH
  * use python2 explicitly to run catkin_make
  * force use of python2 executable by catkin packages
  * python!
  * simpler
  * how to which
  * Update .travis.yml
  * make tests and run_tests
  * test results
  * disable timer tests on macOS
* Fix CMake warning for rt and pthread. (`#165 <https://github.com/clearpathrobotics/serial-ros2/issues/165>`_)
* remove references to no longer available uninstall command (`#171 <https://github.com/clearpathrobotics/serial-ros2/issues/171>`_)
* sublime project file updates
* print GetLastError() result instead of errno (`#154 <https://github.com/clearpathrobotics/serial-ros2/issues/154>`_)
* implement flushInput and flushOutput for windows (`#153 <https://github.com/clearpathrobotics/serial-ros2/issues/153>`_)
* Problem: hardware flow control uses RTS_CONTROL_TOGGLE (`#132 <https://github.com/clearpathrobotics/serial-ros2/issues/132>`_)
  RTS_CONTROL_HANDSHAKE raises RTS when there is space in the input
  buffer; RTS_CONTROL_TOGGLE only raises RTS when bytes are available for
  transmission.
  Also replace numeric constants with symbolic constants.
* Support 500kbps serial ports. (`#167 <https://github.com/clearpathrobotics/serial-ros2/issues/167>`_)
* Fix issue with write() and a timeout of 0. (`#137 <https://github.com/clearpathrobotics/serial-ros2/issues/137>`_)
  * Fix issue with write() and a timeout of 0.
  * fix up style
* Update documentation (`#140 <https://github.com/clearpathrobotics/serial-ros2/issues/140>`_)
  * Fix typo and missing dependency in README
  * [docs] Update docs: fix deprecation warnings + add missing deps to README
* fixing unix timeouts handling ("timer_tests.short_interval" failure) (`#147 <https://github.com/clearpathrobotics/serial-ros2/issues/147>`_)
* fix timeouts handling on Unix systems (`#142 <https://github.com/clearpathrobotics/serial-ros2/issues/142>`_)
  fixed "singed long" overflow that took place on attempt
  to use ~3000ms or bigger timeouts on Unix systems
* resource leak if exception in SerialImpl constructor (`#146 <https://github.com/clearpathrobotics/serial-ros2/issues/146>`_)
* Const corrections. (`#141 <https://github.com/clearpathrobotics/serial-ros2/issues/141>`_)
* Updated serial.cc for FreeBSD 9 compatibility.
* on OS X, use SYSTEM_CLOCK, not CALENDAR_CLOCK
  Analogously to using `CLOCK_MONOTONIC` on Linux to time events in favor of `CLOCK_REALTIME`, `SYSTEM_CLOCK` should be used in favor of `CALENDAR_CLOCK` on OS X.
  Ref: http://stackoverflow.com/questions/11680461/monotonic-clock-on-osx
* on Linux, use CLOCK_MONOTONIC for clock_gettime()
  On Linux systems which are being driven by an external time source (NTP or PTP), it is possible that time appears to slew in reverse under `CLOCK_REALTIME`. Since the timer function is used to time durations of events (calls to `select()`), it is better to use `CLOCK_MONOTONIC`, which isn't subject to slewing.
* Comment unreferenced formal parameter
  Fix warning from static analysis tools.
* Can use the toolsets from Visual Studio 2010, 2012, 2013, 2015
* AdditionalIncludeDirectories must be relative for project not solution
  Fixes `#105 <https://github.com/clearpathrobotics/serial-ros2/issues/105>`_
* Fix include directory paths in Visual Studio projects.
  Remove previously ignored *.user file.
* fix warning on Windows
* Contributors: Ben Moyer, Brandon Morton, Christopher Baker, Dan Rose, José Manuel Díez, Linquize, Mike Purvis, Patrick O'Leary, Rami, Rimco, Scott K Logan, Stephane Poirier, Vladimir Gamalian, William Woodall, aleksey-sergey, bsbaliga, dontsovcmc, rhd

1.2.1 (2015-04-21)
------------------
* Removed the use of a C++11 feature for compatibility with older browsers.
* Fixed an issue with cross compiling with mingw on Windows.
* Restructured Visual Studio project layout.
* Added include of ``#include <AvailabilityMacros.h>`` on OS X (listing of ports).
* Fixed MXE for the listing of ports on Windows.
* Now closes file device if ``reconfigureDevice`` fails (Windows).
* Added the MARK/SPACE parity bit option, also made it optional.
  Adding the enumeration values for MARK and SPACE was the only code change to an API header.
  It should not affect ABI or API.
* Added support for 576000 baud on Linux.
* Now releases iterator properly in listing of ports code for OS X.
* Fixed the ability to open COM ports over COM10 on Windows.
* Fixed up some documentation about exceptions in ``serial.h``.

1.2.0 (2014-07-02)
------------------
* Removed vestigial ``read_cache_`` private member variable from Serial::Serial
* Fixed usage of scoped locks
  Previously they were getting destroyed immediately because they were not stored in a temporary scope variable
* Added check of return value from close in Serial::SerialImpl::close () in unix.cc and win.cc
* Added ability to enumerate ports on linux and windows.
  Updated serial_example.cc to show example of port enumeration.
* Fixed compile on VS2013
* Added functions ``waitReadable`` and ``waitByteTimes`` with implemenations for Unix to support high performance reading
* Contributors: Christopher Baker, Craig Lilley, Konstantina Kastanara, Mike Purvis, William Woodall

1.1.7 (2014-02-20)
------------------
* Improved support for mingw (mxe.cc)
* Fix compilation warning
  See issue `#53 <https://github.com/wjwwood/serial/issues/53>`_
* Improved timer handling in unix implementation
* fix broken ifdef _WIN32
* Fix broken ioctl calls, add exception handling.
* Code guards for platform-specific implementations. (when not using cmake / catkin)
* Contributors: Christopher Baker, Mike Purvis, Nicolas Bigaouette, William Woodall, dawid

1.1.6 (2013-10-17)
------------------
* Move stopbits_one_point_five to the end of the enum, so that it doesn't alias with stopbits_two.

1.1.5 (2013-09-23)
------------------
* Fix license labeling, I put BSD, but the license has always been MIT...
* Added Microsoft Visual Studio 2010 project to make compiling on Windows easier.
* Implemented Serial::available() for Windows
* Update how custom baudrates are handled on OS X
  This is taken from the example serial program on Apple's developer website, see:
  http://free-pascal-general.1045716.n5.nabble.com/Non-standard-baud-rates-in-OS-X-IOSSIOSPEED-IOCTL-td4699923.html
* Timout settings are now applied by reconfigurePort
* Pass LPCWSTR to CreateFile in Windows impl
* Use wstring for ``port_`` type in Windows impl

1.1.4 (2013-06-12 00:13:18 -0600)
---------------------------------
* Timing calculation fix for read and write.
  Fixes `#27 <https://github.com/wjwwood/serial/issues/27>`_
* Update list of exceptions thrown from constructor.
* fix, by Thomas Hoppe <thomas.hoppe@cesys.com>
  For SerialException's:
  * The name was misspelled...
  * Use std::string's for error messages to prevent corruption of messages on some platforms
* alloca.h does not exist on OpenBSD either.

1.1.3 (2013-01-09 10:54:34 -0800)
---------------------------------
* Install headers

1.1.2 (2012-12-14 14:08:55 -0800)
---------------------------------
* Fix buildtool depends

1.1.1 (2012-12-03)
------------------
* Removed rt linking on OS X. Fixes `#24 <https://github.com/wjwwood/serial/issues/24>`_.

1.1.0 (2012-10-24)
------------------
* Previous history is unstructured and therefore has been truncated. See the commit messages for more info.
