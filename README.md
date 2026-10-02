# FleetCheck – Build Systems Lab

This project is intentionally incomplete. Follow the worksheet in the order given.

Expected final application output:

```
FleetCheck 1.0
Vehicles loaded: 4
Vehicles requiring service: 2
Average mileage: 37000 km
```

Do not copy the solution POM. The objective is to observe how each build change alters the result.



8.1: 
C:\Users\grima\Documents\2026-27\Software Quality\TP4\FleetCheck_Gradle\FleetCheck_Gradle\src\main\java\pt\upt\fleetcheck\App.java:4: error: package com.fasterxml.jackson.databind does not exist


Step 3: 
[INFO] \- com.fasterxml.jackson.core:jackson-databind:jar:2.22.2:compile
[INFO]   +- com.fasterxml.jackson.core:jackson-annotations:jar:2.22:compile
[INFO]   \- com.fasterxml.jackson.core:jackson-core:jar:2.22.2:compile


8.2: 
jackson-databind is direct, since it is the dependecy we stated we needed. jackson-annotations and jackson-core are transitive since they are the dependencies that are automatically brought by Gradle in order for jackson-databind to work.

Changing the build system did not change the application dependencies. Both Gradle and Maven evaluate the same external library and pulldown the same dependecy tree.


8.3:
Before the change, the JAR file was incomplete, it lacked the instruction that declared the 'App.java' as the main class. It was also missing tools to be able to read the JSON file.
After the fix, the JAR file is complete and would compile normally across devices.


8.4: 
The Gradle Wrapper removes the assumption that the developer already has the right version of Gradle pre-installed on their system. This way, running the wrapper, the program automatically downloads and uses the correct version of Gradle for this program.

Step 5:
Removes the assumption that my computer has a manually installed version of Maven and it forces the download/usage of the right version for this project.

Step 7:
The bom.json file contains annotations that were not explicitly input since they are transitive dependencies, meaning, jackson-databind (the one we requested) requires lower level libraries (jackson-core and jackson-annotations) in order to function properly. Maven automatically resolved these dependencies. 