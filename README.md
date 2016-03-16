# Jenkins JUnit Analyzer

My personal analyzer for Jenkins JUnit test failures.

Currently will:
* interrogate the specified Jenkins job on the specified server
* download results locally
  * currently stored in local sqlite db
  * this is incremental, we don't d/l the same information again

* analyze the local information looking for:
  * passed vs failed jobs
  * identify which tests (needs to be JUnit today) within the job are failing more frequently than others. Typically these are called "flakey" tests.


Tools:
* localize_job_results.py - localize the jenkins junit results locally
* generate_job_histogram.py - print various histograms for a job based on localized information


Schema:

SQLite is used as a persistent store. It currently supports a single Jenkins server (the schema assumes jobs are from a single jenkins server).

Relationship (parent to child) is: job->build->test

Job Table:
id int
jobname string

Build Table:
id int
jobid int
buildnumber int
result string (pass/fail)

Test Table:
id int
buildid id
test string
result string (pass/fail)
