# kettle-neo4j-integration

Integration tests for the Kettle Neo4j plugins

# Configuration

Set the following variables in your environment:

* NEO_HOSTNAME
* NEO_USERNAME
* NEO_PASSWORD
* NEO_BOLT_PORT

Point them to your test-Neo4j instance of choice.
**WARNING** The data in this instance will be removed prior to testing.  These integration tests start from a blank database. Typically we start up Neo4j in a docker instance for this.

# Usage

Run the job "daily-run.kjb" in the tests/ folder.
After the execution you can find the results in the file "output/results_<date>.csv"

# Adding more tests

If you want to add your own tests, create a new folder containing one or more jobs with the filename starting with "main".
If you define a parameter called "TEST_FOLDER" in these jobs you get the current folder name which you can pass to transformation "shared/validate-tests-in-folder.ktr".
This transformation will run all the unit tests defined on all the transformations in the given folder.

Typically the jobs create, merge, match/set data in Neo4j with the various plugins. The data is then read back out in a series of validation transformations on which we define unit tests to match against golden data.

