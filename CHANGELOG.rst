^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package rclrs_tests
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.3.2
-----------
* Return Arc from the create_node function to match other create_X functions (`#294 <https://github.com/marcoag/ros2_rust/issues/294>`_)
  * Fine-grained locks. Made create_subscription, create_service, create_client not take a mutable self
  * Return an Arc from rclrs::create_node to match other create_X functions
  * Update spin* to take an Arc
  * Fix clippy warning
* Contributors: Esteve Fernandez

0.3.1 (2022-10-17)
------------------
* Version 0.3.1 (`#285 <https://github.com/marcoag/ros2_rust/issues/285>`_)
* Fix a bug in graph query function and add regression test (`#283 <https://github.com/marcoag/ros2_rust/issues/283>`_)
* Contributors: Nikolai Morin

0.3.0 (2022-10-03)
------------------
* Format all code with group_imports = StdExternalCrate (`#272 <https://github.com/marcoag/ros2_rust/issues/272>`_)
* Bump package versions to 0.3 (`#274 <https://github.com/marcoag/ros2_rust/issues/274>`_)
* Extend SubscriptionCallback trait to ReadOnlyLoanedMessage (`#266 <https://github.com/marcoag/ros2_rust/issues/266>`_)
  This was not a straightforward extension because
  1. ReadOnlyLoanedMessage has a lifetime
  2. The take_loaned_message() method was restricted to Subscription<T: RmwMessage>, i.e. not available
  for subscriptions on idiomatic messages.
  This has been fixed and now the method is implemented for Subscription<T: Message> like the other
  `take*` methods – though you still will get an RMW-native loaned message even if T is the idiomatic
  message type, because idiomatic message types can never be loaned.
* Generalize callbacks for subscriptions (`#260 <https://github.com/marcoag/ros2_rust/issues/260>`_)
  * Generalize callbacks to subscriptions
  By implementing a trait (SubscriptionCallback) on valid function signatures,
  and making subscriptions accept callbacks that implement this trait, we can now
  * Receive both plain and boxed messages
  * Optionally receive a MessageInfo along with the message, as the second argument
  * Soon, receive a loaned message instead of an owned one
  This corresponds to the functionality in any_subscription_callback.hpp in rclcpp.
* Test for Send and Sync implementations, and add missing implementations (`#254 <https://github.com/marcoag/ros2_rust/issues/254>`_)
* Add `rclrs_test` package for unit/integration tests (`#239 <https://github.com/marcoag/ros2_rust/issues/239>`_)
  This package is meant to test behaviors with dependencies that don't
  belong in the rclrs crate - namely, msgs
* Contributors: Nikolai Morin, christopherjreid

0.2.0 (2022-07-21)
------------------
