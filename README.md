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