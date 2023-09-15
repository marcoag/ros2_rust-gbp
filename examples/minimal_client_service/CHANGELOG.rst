^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package examples_rclrs_minimal_client_service
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
* Fix build errors in examples_rclrs_minimal_client_service (`#220 <https://github.com/marcoag/ros2_rust/issues/220>`_)
* Added support for clients and services (`#146 <https://github.com/marcoag/ros2_rust/issues/146>`_)
  * Added support for clients and services
* Contributors: Esteve Fernandez, Nikolai Morin
