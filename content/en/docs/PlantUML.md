<!---md
---
date: 2021-11-19:50:19-03:00
title: "Samples Diagrams.md"
description: "Some sample examples of UML/C4Model/MindMap diagrams in Markdown"
hide_feedback: false
toc_hide: true
weight: 10
menu:
  main:
    weight: 10
    pre: <i class='fas fa-chart-line'></i>
---
md--->
# PlantUML demo

> *"PlantUML in a nutshell. PlantUML is a component that allows to quickly write: Sequence diagram. Usecase diagram. Class diagram. Object diagram. Activity diagram (here is the legacy syntax) Component diagram. Deployment diagram"* - [PlantUML.com](http://PlantUML.com).

## Getting started

### Sequence Diagram

```plantuml

Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response

```

- Declaring participant

```plantuml
actor Bob #red
' The only difference between actor
'and participant is the drawing
participant Alice
participant "I have a really\nlong name" as L #99FF99
/' You can also declare:
   participant L as "I have a really\nlong name"  #99FF99
  '/

Alice->Bob: Authentication Request
Bob->Alice: Authentication Response
Bob->L: Log transaction
```

### MindMap Diagram

- Mindmap OrgMode syntax

```plantuml
@startmindmap
* Debian
** Ubuntu
*** Linux Mint
*** Kubuntu
*** Lubuntu
*** KDE Neon
** LMDE
** SolydXK
** SteamOS
** Raspbian with a very long name
*** <s>Raspmbc</s> => OSMC
*** <s>Raspyfi</s> => Volumio
@endmindmap
```

### C4 Model Diagram

> *"The C4 model was designed to help describe, document, and diagram custom-built, bespoke software systems. From this perspective, the C4 model can be used to describe a variety of software architectures (monolithic or distributed), built in a variety of programming languages, deployed on a variety of platforms (on-premises or cloud)"* - [C4Model.com](http://C4Model.com).

```plantuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Person(admin, "Administrator")
System_Boundary(c1, "Sample System") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
```

#### C4 Model Diagram (decorated)

```plantuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

!define DEVICONS https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/devicons
!define FONTAWESOME https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/font-awesome-5
!include DEVICONS/angular.puml
!include DEVICONS/java.puml
!include DEVICONS/msql_server.puml
!include FONTAWESOME/users.puml

LAYOUT_WITH_LEGEND()

Person(user, "Customer", "People that need products", $sprite="users")
Container(spa, "SPA", "angular", "The main interface that the customer interacts with", $sprite="angular")
Container(api, "API", "java", "Handles all business logic", $sprite="java")
ContainerDb(db, "Database", "Microsoft SQL", "Holds product, order and invoice information", $sprite="msql_server")

Rel(user, spa, "Uses", "https")
Rel(spa, api, "Uses", "https")
Rel_R(api, db, "Reads/Writes")
```
