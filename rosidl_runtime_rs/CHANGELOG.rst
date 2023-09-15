^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package rosidl_runtime_rs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.3.2
-----------
* - Upgraded bindgen to 0.66.1 (`#323 <https://github.com/marcoag/ros2_rust/issues/323>`_)
  - Upgraded libloading to 0.8
  - Added instructions to rerun build scripts if dependent files have changed
  - Enabled bindgen to invalidate the built crate whenever any transitively included header files from the wrapper change
  - Removed some default true options from our bindgen builder
  Co-authored-by: Sam Privett <sam@privett.dev>
* Improve efficiency of deserializing strings (`#300 <https://github.com/marcoag/ros2_rust/issues/300>`_)
* Extend string types (`#293 <https://github.com/marcoag/ros2_rust/issues/293>`_)
* Remove libc dependencies (`#284 <https://github.com/marcoag/ros2_rust/issues/284>`_)
* Contributors: Nikolai Morin, Sam Privett, Tatsuro Sakaguchi

0.3.1 (2022-10-17)
------------------
* Version 0.3.1 (`#285 <https://github.com/marcoag/ros2_rust/issues/285>`_)
* Add TYPE_NAME constant to messages and make error fields public (`#277 <https://github.com/marcoag/ros2_rust/issues/277>`_)
* Contributors: Nikolai Morin

0.3.0 (2022-10-03)
------------------
* Format all code with group_imports = StdExternalCrate (`#272 <https://github.com/marcoag/ros2_rust/issues/272>`_)
* Add README files for rclrs and rosidl_runtime_rs (`#273 <https://github.com/marcoag/ros2_rust/issues/273>`_)
  These files will be shown by crates.io.
* Bump package versions to 0.3 (`#274 <https://github.com/marcoag/ros2_rust/issues/274>`_)
* Generalize callbacks for subscriptions (`#260 <https://github.com/marcoag/ros2_rust/issues/260>`_)
  * Generalize callbacks to subscriptions
  By implementing a trait (SubscriptionCallback) on valid function signatures,
  and making subscriptions accept callbacks that implement this trait, we can now
  * Receive both plain and boxed messages
  * Optionally receive a MessageInfo along with the message, as the second argument
  * Soon, receive a loaned message instead of an owned one
  This corresponds to the functionality in any_subscription_callback.hpp in rclcpp.
* Add support for loaned messages (`#212 <https://github.com/marcoag/ros2_rust/issues/212>`_)
* Implement Message for Box<T: Message>  (`#235 <https://github.com/marcoag/ros2_rust/issues/235>`_)
* Fixes for releasing to crates.io (`#231 <https://github.com/marcoag/ros2_rust/issues/231>`_)
  * Fixups for releasing to crates.io
  * Removed std_msgs as test dependency. Fix rosidl_runtime_rs version
  * Removed test
  * Removed test
* Contributors: Esteve Fernandez, Nikolai Morin, Raghav Mishra

0.2.0 (2022-07-21)
------------------
* Added support for clients and services (`#146 <https://github.com/marcoag/ros2_rust/issues/146>`_)
  * Added support for clients and services
* Fix a portability problem in rosidl_runtime_rs::String (`#219 <https://github.com/marcoag/ros2_rust/issues/219>`_)
  Previously, it was assumed by the $string_conversion_func, for instance, that the output of deref() would be an unsigned integer.
* Add unit testing (`#84 <https://github.com/marcoag/ros2_rust/issues/84>`_)
  * Copied tests from jhdcs' fork
  * Ran cargo fmt
  * Run clippy on tests as well
  * Make Clippy happy
  * Fix rustfmt warning
  * Added std_msgs to package.xml
  * Disable deref_nullptr warning for generated code
  * Include Soya-Onishi's changes
  * Fix Node::new call
  * Fix spelling mistakes
  Co-authored-by: jhdcs <48914066+jhdcs@users.noreply.github.com>
  * Fix spelling mistakes
  Co-authored-by: jhdcs <48914066+jhdcs@users.noreply.github.com>
  * Fix spelling mistakes
  Co-authored-by: jhdcs <48914066+jhdcs@users.noreply.github.com>
  * Fix formatting
  Co-authored-by: jhdcs <48914066+jhdcs@users.noreply.github.com>
* Add Nikolai and Jacob to authors in Cargo.toml and maintainers in package.xml (`#133 <https://github.com/marcoag/ros2_rust/issues/133>`_)
* Make all the things Send, and messages Sync as well (`#171 <https://github.com/marcoag/ros2_rust/issues/171>`_)
  This is required to make multithreading work. For instance, calling publish() on a separate thread doesn't work without these impls.
* Rename RMW-compatible to RMW-native (`#159 <https://github.com/marcoag/ros2_rust/issues/159>`_)
* Add serde support to messages (`#131 <https://github.com/marcoag/ros2_rust/issues/131>`_)
* Add comments explaining each dependency (`#122 <https://github.com/marcoag/ros2_rust/issues/122>`_)
* Removed support for no_std (`#109 <https://github.com/marcoag/ros2_rust/issues/109>`_)
  * Removed support for no_std
  * Removed more no_std dependencies
  * Removed more no_std dependencies
  * Removed more no_std dependencies
  * Removed downcast
  * Removed TryFrom, not needed with Rust 2021
  * Fix visibility of modules
* Document all public items (`#94 <https://github.com/marcoag/ros2_rust/issues/94>`_)
* Bump every package to version 0.2 (`#100 <https://github.com/marcoag/ros2_rust/issues/100>`_)
* Give subscription callback the owned message (`#92 <https://github.com/marcoag/ros2_rust/issues/92>`_)
  Also remove unused dependency from rosidl_runtime_rs
* Enable Clippy in CI (`#83 <https://github.com/marcoag/ros2_rust/issues/83>`_)
* Message generation refactoring (`#80 <https://github.com/marcoag/ros2_rust/issues/80>`_)
  Previously, only messages consisting of basic types and strings were supported. Now, all message types will work, including those that have fields of nested types, bounded types, or arrays.
  Changes:
  - The "rsext" library is deleted
  - Unused messages in "rosidl_generator_rs" are deleted
  - There is a new package, "rosidl_runtime_rs", see below
  - The RMW-compatible messages from C, which do not require an extra conversion step, are exposed in addition to the "idiomatic" messages
  - Publisher and subscription are changed to work with both idiomatic and rmw types, through the unifying `Message` trait
  On `rosidl_runtime_rs`: This package is the successor of `rclrs_msg_utilities` package, but doesn't have much in common with it anymore.
  It provides common types and functionality for messages. The `String` and `Sequence` types and their variants in that package essentially wrap C types from the `rosidl_runtime_c` package and C messages generated by the "rosidl_generator_c" package.
  A number of functions and traits are implemented on these types, so that they feel as ergonomic as possible, for instance, a `seq!` macro for creating a sequence. There is also some documentation and doctests.
  The memory for the (non-pretty) message types is managed by the C allocator.
  Not yet implemented:
  - long double
  - constants
  - Services/clients
  - @verbatim comments
  - ndarray for sequences/arrays of numeric types
  - implementing `Eq`, `Ord` and `Hash` when a message contains no floats
* Contributors: Esteve Fernandez, Nikolai Morin
