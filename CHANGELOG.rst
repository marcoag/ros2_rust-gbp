^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package examples_rclrs_minimal_pub_sub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.3.2
-----------
* Refactor spin and spin_once to mimic rclcpp's Executor API (`#324 <https://github.com/marcoag/ros2_rust/issues/324>`_)
  * Added rclcpp/rclpy-like executor
  * Fix comments
* Return Arc from the create_node function to match other create_X functions (`#294 <https://github.com/marcoag/ros2_rust/issues/294>`_)
  * Fine-grained locks. Made create_subscription, create_service, create_client not take a mutable self
  * Return an Arc from rclrs::create_node to match other create_X functions
  * Update spin* to take an Arc
  * Fix clippy warning
* Contributors: Esteve Fernandez

0.3.1 (2022-10-17)
------------------
* Version 0.3.1 (`#285 <https://github.com/marcoag/ros2_rust/issues/285>`_)
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
* Add support for loaned messages (`#212 <https://github.com/marcoag/ros2_rust/issues/212>`_)
* Contributors: Nikolai Morin

0.2.0 (2022-07-21)
------------------
* Added support for clients and services (`#146 <https://github.com/marcoag/ros2_rust/issues/146>`_)
  * Added support for clients and services
* Move create_node and create_node_builder back to the rclrs module (`#200 <https://github.com/marcoag/ros2_rust/issues/200>`_)
  * Move create_node and create_node_builder back to the rclrs module
  * Fix tests
  * Fix tests
  * Fix formatting
* feat: add example launch (`#187 <https://github.com/marcoag/ros2_rust/issues/187>`_)
  * feat: add example launch
  * docs: fix README.md
  Co-authored-by: Nikolai Morin <nnmmgit@gmail.com>
  Co-authored-by: Nikolai Morin <nnmmgit@gmail.com>
* Add Nikolai and Jacob to authors in Cargo.toml and maintainers in package.xml (`#133 <https://github.com/marcoag/ros2_rust/issues/133>`_)
* Move rclrs_examples to examples/minimal_pub_sub (`#163 <https://github.com/marcoag/ros2_rust/issues/163>`_)
* Contributors: Daisuke Nishimatsu, Esteve Fernandez, Nikolai Morin
