This project consists of three modules: `aggregator`, `parent` and `child`. `aggregator` 
aggregates the two other projects, `parent` is the parent project of `child`. Notably, `aggreagator`
is not the parent project.

Running `mvn clean site site:stage` yields the following output:

```
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] parent                                                             [pom]
[INFO] child                                                              [jar]
[INFO] aggregator                                                         [pom]
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ parent ---
[INFO] Using this base directory for staging: C:\temp\foo
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\parent\target\site
[INFO]    >>> to file://C:\temp\foo/./
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ child ---
[INFO] Using this base directory for staging: C:\temp\foo
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\child\target\site
[INFO]    >>> to file://C:\temp\foo/../child
[...]
[INFO] --- site:3.21.0:stage (default-cli) @ aggregator ---
[INFO] Using this base directory for staging: C:\temp\foo
[INFO] Pushing D:\programming\maven-site-test-aggregator-parent-separate\target\site
[INFO]    >>> to file://C:\temp\foo/./
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for aggregator 1.0-SNAPSHOT:
[INFO] 
[INFO] parent ............................................. SUCCESS [  3.871 s]
[INFO] child .............................................. SUCCESS [  0.690 s]
[INFO] aggregator ......................................... SUCCESS [  0.615 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[...]
```