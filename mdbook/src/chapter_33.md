# Interfaces
@startuml 
skinparam backgroundColor transparent
left to right direction

component Interfaces_diagram {
    
    [frame]
    () placement -u- frame
    [Cylinder]
    () "contact\nsensor" -- Cylinder

    [sensor]
    sensor --> "sensor\nposition"
    
    Cylinder -> placement

    [Cylinder]
    () "Cylinder\npower" -- room
    () "Haul_Off\npower" -- room
   
    room -u-> placement
    Cylinder --> "Cylinder\npower"
    
    [Haul_Off]
    () "sensor\nposition" -- Haul_Off
    () "Thermoplastic\nposition" -- Haul_Off
    Haul_Off -> placement
    Haul_Off --> "Haul_Off\npower"

    [Thermoplastic]
    () shape -- Thermoplastic
    
    [press]
    press -l-> shape
    
    Thermoplastic --> "Thermoplastic\nposition"
    press --> "contact\nsensor"

    [Infrared_lamp]
    Infrared_lamp -> room
    Thermoplastic -->Infrared_lamp
    
    [Extruder]
    Extruder --> room
    Thermoplastic --> Extruder
    
    [Safety_Alarm]
    Safety_Alarm --> room
    Safety_Alarm --> Cylinder
    Safety_Alarm --> Haul_Off
    Safety_Alarm --> Extruder
     
    [Rails]
    Rails --> press
    Rails --> room

    [Synchronization_Board]
    Synchronization_Board --> Rails
    Synchronization_Board --> Cylinder
    Synchronization_Board --> Haul_Off
    Synchronization_Board --> Extruder
    Synchronization_Board --> room
    Synchronization_Board --> Safety_Alarm

}

[building]

() energy -l- building
() location -d- building

frame --> location
room -r-> energy

@enduml

```plantuml
@startuml 
skinparam backgroundColor transparent
left to right direction

component Interfaces_diagram {
    
    [Cylinder]
    () "contact\nsensor" -- Cylinder

    [Cylinder]
    () "Cylinder\npower" -- room
    () "Haul_Off\npower" -- room
   
    Cylinder --> "Cylinder\npower"
    Cylinder --> shape
    

    [Haul_Off]
    () "Thermoplastic\nposition" -- Haul_Off
    Haul_Off --> "Haul_Off\npower"
    [Thermoplastic]
    () shape -- Thermoplastic
    
    [press]
    press -l-> shape

    Thermoplastic --> "Thermoplastic\nposition"
    press --> "contact\nsensor"

    [Infrared_lamp]
    Infrared_lamp -> room
    Thermoplastic -->Infrared_lamp
    
    [Extruder]
    Extruder --> room
    Thermoplastic --> Extruder
     
    [Rails]
    Rails --> room
    press --> Rails

    [Synchronization_Board]
    Synchronization_Board --> Rails
    Synchronization_Board --> Cylinder
    Synchronization_Board --> Haul_Off
    Synchronization_Board --> Extruder
    Synchronization_Board --> room
    Synchronization_Board --> Safety_Alarm
 

}
room -r-> energy

@enduml
```