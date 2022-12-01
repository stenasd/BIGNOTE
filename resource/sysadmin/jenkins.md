k8s 
automation layer to jenkins

ugly robot that help ensure quality of codebase as things are added
highlevel scheduling and queing commands based on triggers

- listens for new Pull Requests (finished features that are awaiting testing)

- merges work/feature branches into the mainline (master) branch

- runs a couple of automated test suites on the code which now includes the work branch

- creates and seeds a new test database for each run of the test suite, then immediately deletes it

- reports any failures in the test suite via email and HipChat

- runs code through a static analysis tool and reports the findings

- deploys the latest code changes to a QA environment for manual testing

todo bookbook
creat tests
run with jenkins mock database
test search,

https://www.jenkins.io/doc/tutorials/build-a-node-js-and-react-app-with-npm/#run-jenkins-in-docker
https://qaautomationlabs.com/how-run-playwright-test-case-in-jenkins-pipelines/