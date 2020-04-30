# Traffic Simulator
## Program Development Process

### Problem Specification
The client is required to be able to simulate traffic in a city environment by making use of various vehicles, roads,
intersections and traffic lights. This traffic simulation would be done in the console. The console would help to 
showcase the status of all objects in the simulator. The simulator would show various actions such as: a vehicle
navigating through different roads and their intersections, the speeds in which they travel and reacting to traffic 
lights according to their current traffic light colors.

### Problem Decomposition
As mentioned above, vehicles, roads and traffic lights would be used in the traffic simulator. These objects would 
interact with one another to produce the intended actions. The following showcases each object and the attributes they
consist of.

####Vehicle
The vehicle class is an object that could either be a car, bus or motorbike.<br /><br /> 
The vehicle class has the following attributes:
- *id* - an identification number that uniquely identifies each vehicle.
- *Length, Breadth* - The dimensions of the vehicle.
- *Location* - The exact place where the vehicle is located at. 
- *Road Location* - The road in which the vehicle is currently travelling on.
- *Speed* - How fast a vehicle moves.
- *Spawn Location* - Location in which the vehicle first enters the simulator.
- *Location on Red Light* - Location where a vehicle stops if it is approaching a traffic light that has turned red.
- *Move Direction* - Direction in which the vehicle chooses to take when travelling through an intersection.

A method would first be called so that each vehicle would be able to move. Upon approaching a traffic light, 
another method wil be called to check the state of that specific traffic light. If the light is red, the vehicle would 
stop at the "Location on red light" attribute. If the light is green, the vehicle would proceed onto the next road. 
Upon reaching the center of the intersection, a method would be called to see which direction the vehicle would like 
to go. The direction in which the vehicle takes is random. This process will continue until there are no more connected 
roads for the vehicle to travel on thus, ending the traffic simulator.


#### Road
The road class is an object that could either be a straight intersection, 3-way intersection or 4-way intersection.
<br /><br />
The road class has the following attributes:
- *id* - an identification number that uniquely identifies each road.
- *length* - The length of each road.
- *Intersection Point* - The point where a vehicle stops and turns if it is changing directions.
- *Start Position* - The position where the road begins.
- *End Position* - The position where the road ends.
- *Linked Roads* - List of all of the other roads that are connected to this road.
- *Linked Traffic Lights* - List of all traffic lights that are connected to the road.
- *Current Vehicles on road* - List of all vehicles that are currently on the road.

For simplicity when navigating through the roads and traffic lights, all vehicle speeds would be set to 1 and would 
remain at that speed throughout the duration of its life. Roads can only interact with other roads that are directly
linked with them. Vehicles would enter the road at its start position and leave the road at its end position. 
Furthermore, only some roads have traffic lights. These traffic lights can only be found at the end position of these
roads. 

#### Traffic Light
The traffic light class is an object where its color could either be red or green. <br /><br />
The traffic light class has the following attributes:
- *id* - an identification number that uniquely identifies each road.
- *red light* - whenever the traffic light turns red.
- *green light* - whenever the traffic light turns green.
- *Light Change Duration* - how long it takes before the traffic light changes its color.
- *Road Location* - the road in which the traffic light is connected to.
- *Position* - The position in which the traffic light is located on the road.

A method would first be called to start operating the traffic light with the light initially turning green. 
After a certain fixed amount of time, the traffic light would then turn to red. Each traffic light is positioned at the 
end of the road that it is connected to. When a vehicle approaches each traffic light, the vehicle would have to first 
ensure that the traffic light is green before moving on to the next road. The vehicle would have to stop if the traffic
light is red.  

### Main
The main class would have the main() method which will create the entire traffic simulator process. All vehicles, roads
and traffic light objects would be created in this method. This method starts running with the vehicles spawning 
into the simulator and would stop running once the vehicle comes to a stop at the end of the road when there are no 
further roads available.