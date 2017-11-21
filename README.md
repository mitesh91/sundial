# Sundial

What is Sundial?

Sundial is a batch job scheduler for running Dockerized batch jobs on either Amazon ECS or recently, AWS Batch

Think of Sundial as an alternative to Chronos that uses Amazon ECS instead of Mesos and has some nice extra features.

Authors: [CONTRIBUTORS.md](CONTRIBUTORS.md)

Features:

  * Supports dependency graph of tasks within a process.
  * Live viewer for viewing logs streamed to Cloudwatch from job.
  * Job logs and Docker logs collected and uploaded to S3 at end of run for later browsing through Sundial.
  * Graphite metadata server so jobs can upload metrics.
  * Automatic retries for failed tasks within process flows
  * E-mail notifications at end of process runs
  * Supports running Dockerized tasks and shell commands

# Getting started.

Set up Sundial service and ECS cluster using Cloudformation template. See [DEPLOY.md](docs/DEPLOY.md) for details.

Submit your jobs using REST API. See description of job JSON format under [JOBS.md](docs/JOBS.md)

The latest API is hosted here: https://app.apibuilder.io/gilt/svc-sundial/latest
A prettier version of the API can be seen at: http://ui-www.apibuilder.io.s3-website-us-east-1.amazonaws.com/org/gilt/app/svc-sundial
