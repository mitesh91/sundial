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

## Running Sundial Local

For development purposes it's possible to run sundial locally via the script `./start-dev.sh`.

Pre-requisites are:

1. create a dev s3 bucket on aws that sundial can access
2. create a .aws.env file at the root of the project with the required env variables (See example below)

### The .aws.env file

The `docker-compose.yml` file used to run sundial locally, contains almost all the config required to 
run sundial on your laptop. Some env variables thou, have to be setup on a case by case scenario.
An example is the following:
```properties
AWS_REGION=us-east-1
AWS_PROFILE=my-aws-profile
SUNDIAL_S3_BUCKET_DEV=sundial-dev-bucket
```

## Deprecation

Please not that very shortly ECS will be removed as a way of running sundial jobs. The new AWS Batch
allows a better, simpler and cheaper way of running batch jobs on aws.
