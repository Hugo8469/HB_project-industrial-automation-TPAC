# Interfaces
```plantuml
@startuml 
skinparam backgroundColor transparent
left to right direction

component box_pickup_application {
    
    [frame]
    () placement -u- frame
    [robot]
    () input_0 -- robot
    () output_0 -- robot
    () "end\neffector" -- robot

    [sensor]
    sensor --> input_0 : connected
    sensor --> "sensor\nposition"
    
    robot -> placement

    [cabinet]
    () "robot\npower" -- cabinet
    () "conveyor\npower" -- cabinet
   
    cabinet -u-> placement
    robot --> "robot\npower"
    cabinet -r-> output_0
    
    [conveyor]
    () "sensor\nposition" -- conveyor
    () "box\nposition" -- conveyor
    conveyor -> placement
    conveyor --> "conveyor\npower"

    [box]
    () shape -- box
    
    [gripper]
    gripper -l-> shape
    
    box --> "box\nposition"
    gripper --> "end\neffector"
}

[building]

() energy -l- building
() location -d- building

frame --> location
cabinet -r-> energy

@enduml
```