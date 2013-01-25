# Twitter Branch

## Description
This file describes the changes merged to the Twitter github branch. All changes made to this
branch (with the exception of this file and build-common.xml, see below), are also pull requests
back to the master. If all pull requests below are merged to master, then this branch should be in
sync with master.

## How To Release

To cut a new release (1.5.0-T1 in this example) make a release branch and build the artifacts.

```
   $ git checkout twitter
   $ git pull
   $ git checkout -b twitter_1.5.0-T1
   $ vi build-common.xml
     // set build.version to 1.5.0-T1
   $ git commit -m "setting version in branch release" build-common.xml
   $ git push origin twitter_1.5.0-T1
   $ ant -Dbuild.version=1.5.0-T1 -Dhadoop.dir=/path/to/hadoop/dir -Dpig.jar=/path/to/pig/jar
```

Then publish the following artifacts:

```
   hadoop-connector/build/hadoop-connector/jar/hadoop-vertica-1.5.0-T1.jar
   pig-connector/build/pig-connector/jar/pig-vertica-1.5.0-T1.jar
```

## Changes From Master:

* Simplifying how build works: [billonahill/improve_build](https://github.com/vertica/Vertica-Hadoop-Connector/pull/2)
* Refactoring to improve per-task transaction isolation: [billonahill/output_committer](https://github.com/vertica/Vertica-Hadoop-Connector/pull/3)
