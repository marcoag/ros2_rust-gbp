^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package examples_rclrs_message_demo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
* Contributors: Nikolai Morin

0.3.0 (2022-10-03)
------------------
* Format all code with group_imports = StdExternalCrate (`#272 <https://github.com/marcoag/ros2_rust/issues/272>`_)
* Bump package versions to 0.3 (`#274 <https://github.com/marcoag/ros2_rust/issues/274>`_)
* Contributors: Nikolai Morin

0.2.0 (2022-07-21)
------------------
* Move create_node and create_node_builder back to the rclrs module (`#200 <https://github.com/marcoag/ros2_rust/issues/200>`_)
  * Move create_node and create_node_builder back to the rclrs module
  * Fix tests
  * Fix tests
  * Fix formatting
* Add function to demonstrate serde integration (`#179 <https://github.com/marcoag/ros2_rust/issues/179>`_)
* Move rclrs_examples to examples/minimal_pub_sub (`#163 <https://github.com/marcoag/ros2_rust/issues/163>`_)
* Contributors: Esteve Fernandez, Nikolai Morin
