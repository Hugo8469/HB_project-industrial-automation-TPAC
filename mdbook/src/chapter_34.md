# Interactions

@startuml ExtrusionProcess
' Title of the diagram
title Extrusion and Material Processing Flow

' Definitions of the main components
component Extruder {
  [Hot Material]
}
component HaulOff as "Haul-Off System" {
  [Pulling Mechanism]
}
component Press as "Press Machine" {
  [Pressing Cylinder]
  [Moving Rails]
  [Processing Area]

}

    component Synchronization{
    [Speed]
    [Rail Position]
    [Cylinder]

}

' Material flow and actions
[Thermoplastic Material] -> [Hot Material] : Material Processed
[Hot Material] --> [Pulling Mechanism] : **Is Extruded**

' Movement and Processing of the Material
[Pulling Mechanism] --> [Processing Area] : Pulled Material

' Description of movements in the Press
[Processing Area] .down.> [Moving Rails] : **Input Position**
[Processing Area] .down.> [Pressing Cylinder] : **Pressing/Opening Action**

[Processing Area] --> [Processed Material] : Finished Material
note right of [Processing Area]
    The material is positioned into the press
    and pressed by the cylinder.
end note

' Legend
legend right
  - [] : State or Product
  - component : Machinery or System
  - --> : Material Flow
  - .> : Mechanical Action or Movement
end legend

'Synchronization of the whole process
[Speed] --> [Pulling Mechanism] : Pulled Material Speed
[Hot Material] --> [Speed] : Pulled Material Speed
[Speed] --> [Moving Rails] : Pulled Material Speed
[Rail Position] --> [Moving Rails] : Initial/Final position
[Cylinder] --> [Pressing Cylinder] : Pressing/Opening action
@enduml


