# Flowchart of the Process

## Extrusion Process Flow Diagram

```plantuml
@startuml
title Linear Extrusion Process Flow

participant "User"
participant "Extruder" as extruder
participant "Infrared Lamp" as InfraredLamp
participant "Linear Rail" as rail
participant "Press" as press
participant "Cylinder" 
participant "Haul Off" as haul_off
participant "Cooling System" as CoolingSystem
participant "Synchronization"


== Initialization ==
User -> Synchronization : Start the machine
extruder -> Synchronization : Material speed
Synchronization -> haul_off : Speed Synchronization
Synchronization -> rail : Speed Synchronization
Synchronization -> Synchronization : Wait until rail position reached
Synchronization -> InfraredLamp : Start heating, and keep the desired position
InfraredLamp -> Synchronization : Temperature reached
Synchronization -> haul_off : Start pullung material
Synchronization -> CoolingSystem : Start colling, and keep to the desire position

== Production Cycle ==
group Continuous Process
    User -> extruder : Start material feed
    
    loop Every cycle
        Synchronization -> rail : Home position
        opt Rail at start position 
        rail -> Synchronization : Initial position reached
        Synchronization -> Cylinder : Close mold
        Synchronization -> rail : Move to end position
        end
        opt Rail at end position
            rail -> Synchronization : Final Position reached
            Synchronization -> Cylinder : Open mold
            Synchronization -> rail : Return to start
        end
    end
end

== Emergency Stop ==
note over extruder, Synchronization
    Any component can trigger E-stop
    All movements stop immediately
end note

@enduml
```

This diagram illustrates the linear extrusion process flow, showing the interaction between:
- Extruder
- Linear Rail System
- Press
- Haul Off
- Cutter

The process includes initialization, continuous production cycle, and emergency stop handling.
