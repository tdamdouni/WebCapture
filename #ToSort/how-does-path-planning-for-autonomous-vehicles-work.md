# How Does Path Planning for Autonomous Vehicles Work

_Captured: 2018-04-25 at 07:30 from [dzone.com](https://dzone.com/articles/how-does-path-planning-for-autonomous-vehicles-wor?edition=375219&utm_source=Zone+Newsletter&utm_medium=email&utm_campaign=iot+2018-04-24)_

Path planning and decision making for [autonomous vehicles in urban environments](https://www.intellias.com/the-emerging-future-of-autonomus-driving/) enable self-driving cars to find the safest, most convenient, and most economically beneficial routes from point A to point B. Finding routes is complicated by all of the static and maneuverable obstacles that a vehicle must identify and bypass. Today, the major path planning approaches include the predictive control model, feasible model, and behavior-based model. Let's first get familiar with some terms to understand how these approaches work.

  * A **path** is a continuous sequence of configurations beginning and ending with boundary configurations. These configurations are also referred to as initial and terminating.
  * **Path planning** involves finding a geometric path from an initial configuration to a given configuration so that each configuration and state on the path is feasible (if time is taken into account).
  * A **maneuver** is a high-level characteristic of a vehicle's motion, encompassing the position and speed of the vehicle on the road. Examples of maneuvers include going straight, changing lanes, turning, and overtaking.
  * **Maneuver planning** aims at taking the best high-level decision for a vehicle while taking into account the path specified by path planning mechanisms.
  * A **trajectory** is a sequence of states visited by the vehicle, parameterized by time and, most probably, velocity.
  * **Trajectory planning** or trajectory generation is the real-time planning of a vehicle's move from one feasible state to the next, satisfying the car's kinematic limits based on its dynamics and as constrained by the navigation mode.

## A Continuous Search of Space and Corridors Determines Successful Path Planning

Path planning for autonomous vehicles becomes possible after technology considers the urban environment in a way that enables it to search for a path. Put simply, the real-life physical environment is transformed into a digital configuration or a state space. Path planning technology searches for and detects the space and corridors in which a vehicle can drive.

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16105848/Cars.jpg)

**These are the major algorithms used for finding corridors and space: **

  * The** Voronoi diagram (a)** algorithm generates paths that maximize the distance between a vehicle and surrounding obstacles.
  * The **occupancy grid (b) **algorithm works similarly to the Voronoi diagram, though risk and feasibility are calculated primarily by considering the presence of obstacles and lane and road boundaries.
  * Whereas the occupancy grid consists almost exclusively of a grid with the obstacle's position, with the **cost maps (c)** algorithm, the higher cost of a cell results in its more intense representation on the map.
  * The** state lattices (d)** algorithm uses a generalization of grids. Grids are built by the repetition of rectangles or squares to discretize a continuous space, while lattices are constructed by regularly repeating primitive paths that connect possible states for the vehicle.
  * The** driving corridors (e)** algorithm recreates continuous collision-free spaces, bounded by lanes and other obstacles between which the vehicle is expected to drive. Driving corridors algorithms use data from digital maps built by Simultaneous Location and Mapping (SLAM) models.

## The Old-Fashioned Mathematics Behind Autonomous Vehicle Path Planning

Let's add a little bit of rocket science to autonomous driving path planning. The model predictive control approach solves a finite-time constrained optimal control problem in a receding horizon. Path planning can, therefore, be formulated as a nonlinear optimization problem:

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16110049/formula.png)

In this formula, **N** marks the prediction horizon while **M** is the number of lanes on the roadway. Equation **1b** is the constraint imposed by the vehicle kinematics; equation **1c** constrains the feasible set of the state, which considers the actuator limits of the vehicle; equation **1d** enforces collision avoidance between the vehicle in question and surrounding vehicles.

Using this mathematical model, the predictive control algorithm can define the most feasible way to change lanes, avoid collisions, and complete other sophisticated maneuvers.

## So, How Does Path Planning for Autonomous Cars Work?

After the route planner generates a path through the road network, the technology's behavioral layer evaluates the surrounding environment and generates the most appropriate motion specification for the trip. Then the motion planner elaborates the feasible driving mode to meet the specification. Finally, the feedback control adjusts the mode in real-time to correct errors and overcome obstacles on the road.

Smooth local path planning for autonomous vehicles is no longer a matter of simply choosing the shortest path from the starting point to the destination. Today, path planning technologies encompass a wide range of aspects to calculate the safest, most convenient, and most efficient route. Put simply, path planning is based on two major elements: behavior prediction of maneuverable objects and behavior planning for the vehicle itself.

### Predicting the Behavior of Maneuverable Objects

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16110823/car-path-planning.png)

Multiple-model algorithms for maneuvering target tracking are used to predict the behavior of all dynamic objects in the space and corridor, and then based on this, to predict the trajectory of each object. These algorithms evaluate multiple possible maneuvers simultaneously for each object, then correlate them with updated on-road observations.

Eventually, the algorithm defines the probability of each potential maneuver by the object. High-probability maneuvers are afterward used to build the expected trajectory. After trajectories are defined, the path planning technology considers the most appropriate vehicle behavior.

### Planning Vehicle Behavior

Behavior planning for vehicles encompasses driving efficiency and the balancing of safety and comfort. Driving efficiency means determining the best lane to reach the destination promptly while comfort means getting to that lane feasibly and safely. Ranking lanes and feasibility checks are therefore the two core elements underlying vehicle behavior planning.

With regard to lane ranking, the algorithm is led by three main principles. First, the fewer lane changes, the better. Second, the larger the distance to the moving object ahead, the better the score for maneuvers. Third, the greater the velocity of the object ahead, the faster the car can drive in the lane. After each possible lane is ranked, their feasibility is defined. The scheme below shows how the algorithm defines feasibility.

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16105859/Shem.jpg)

### The Hierarchical Framework for Path Planning

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16111653/block.png)

Applying the hierarchical model for path planning enables autonomous vehicles to complete long-term missions and reduce the workload of motion planning. In other words, the hierarchical model optimizes the work of path planning technologies.

For each layer of the hierarchy architecture, the input higher-level mission is decomposed into sub-missions and then passed to the next level down. The hierarchical model helps to resolve many complicated problems, yet it might slow down the work of a vehicle's feedback control and complicate the performance of sophisticated maneuvers.

### The Parallel Framework for Path Planning

Compared with the hierarchical model, the processes in the parallel framework for path planning are more independent and can proceed simultaneously. With this framework, each controller has dedicated sensors and actuation mechanisms.

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16111648/block-3.png)

Using the parallel framework has some benefits. First, the controllers are running at a high frequency, making them safe and stable. Second, the controllers achieve a high level of smoothness and performance. Third, the model is relatively inexpensive and doesn't require the use of complicated motion planning devices.

Still, for some purposes, the hierarchical model remains more efficient. For instance, with a parallel framework for path planning, a vehicle may hardly merge into a lane with slower traffic while a car's intended movements aren't consented to by its speed controller.

## Is Path Planning Simple or Not?

Developers have been quite successful in building technologies that provide feasible path planning for autonomous vehicles from the viewpoint of traffic intensity, safety, and economic relevance. But the [market demands for path planning go far beyond these basic features.](https://www.intellias.com/automotive-highlights-furious-ascent-2017-vs-great-expectations-2018/)

![Path Planning for Autonomous Vehicles with Hyperloop Option](https://s3-eu-west-1.amazonaws.com/elasticbeanstalk-eu-west-1-981246043789/wp-content/uploads/2018/03/16111923/car-parking.png)

Automatically generated routes for both human-driven and self-driving vehicles are expected to encompass a wide range of points of interest (POIs) that have little in common with the technical aspects of the drive. For autonomous vehicles, POIs include charging stations, battery replacement points, and repair centers.

If there are passengers in a vehicle, they'll probably want something more to make the trip comfortable. Path planning technology can look for cafes and restaurants close to the route so drivers and passengers don't miss a meal. In addition, path planning technology can evaluate the best ways to pick up passengers or carry freight if necessary. Sophisticated smart planning is about to bring a plethora of new opportunities to previously unrelated OEMs, software vendors, and Tier 1 companies.
