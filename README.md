This project consists of three modules: `aggregator`, `parent` and `child`. `aggregator` 
aggregates the two other projects, `parent` is the parent project of `child`. Notably, `aggreagator`
is not the parent project.

Running `mvn clean site site:stage` yields the following output:

```
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] parent                                                             [pom]
[INFO] child                                                              [jar]
[INFO] aggregator                                                         [pom]
[INFO]
[INFO] --< com.github.seekM.maven-site-test-aggregator-parent-separate:parent >--
[INFO] Building parent 1.0-SNAPSHOT                                       [1/3]
[INFO]   from parent\pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ parent ---
[INFO] Using this base directory for staging: D:\programming\maven-site-test-aggregator-parent-separate\target\staging
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\parent\target\site
[INFO]    >>> to file://D:\programming\maven-site-test-aggregator-parent-separate\target\staging/./
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ child ---
[INFO] Using this base directory for staging: D:\programming\maven-site-test-aggregator-parent-separate\target\staging
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\child\target\site
[INFO]    >>> to file://D:\programming\maven-site-test-aggregator-parent-separate\target\staging/../child
[...]
[INFO] --- clean:3.2.0:clean (default-clean) @ aggregator ---
[INFO] Deleting D:\programming\maven-site-test-aggregator-parent-separate\target
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ aggregator ---
[INFO] Using this base directory for staging: D:\programming\maven-site-test-aggregator-parent-separate\target\staging
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\target\site
[INFO]    >>> to file://D:\programming\maven-site-test-aggregator-parent-separate\target\staging/./
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for aggregator 1.0-SNAPSHOT:
[INFO]
[INFO] parent ............................................. SUCCESS [  3.498 s]
[INFO] child .............................................. SUCCESS [  0.567 s]
[INFO] aggregator ......................................... SUCCESS [  0.528 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[...]
```