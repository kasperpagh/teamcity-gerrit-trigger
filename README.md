Expanded from source: https://github.com/Saulis/teamcity-gerrit-trigger

teamcity-gerrit-trigger
=======================

Plugin for Teamcity which polls Gerrit to trigger builds

#### How it works
- Connects to Gerrit using Gerrits SSH command line API
- Polls for patchsets every 20 seconds (query is limited to fetch only the last 10 patchsets)
- Queues a new build for every new patchset found (new as in created after the last build was queued)

#### Building

- Run getApacheMaven.bat for a one time setup of Apache Maven. (only for Winblows)
- Run mvn package to create a zip file which you can drop under the plugins folder in your Teamcity server.

#### Usage

- After installation, add the _Gerrit Build Trigger_ into your build configuration 
- Configure the trigger:
  - Host: hostname of your Gerrit instance in the form dev.gerrit.com (uses default port 29418, custom ports not supported)
  - Username: SSH username that will be used to open connection (optional, default: the username that runs Teamcity)
  - Custom private key: Full path to the private key you want to use (optional, default: default private key of user)
  - Host Connection Timeout Seconds: The number of seconds that the trigger waits for Gerrit to finish answering
  - Trigger Poll Interval Seconds: The polling Interval
  - Gerrit Review Query Limit: The maximum number of expected patchsets that can appear in between two polling intervals.
  - Project: Filter for querying patchsets (optional)
  - Branch: Filter for querying patchsets (optional)
  - Queue as Personal Build: Will the trigger create "normal" or personal builds in TeamCity. Mostly Applicable for testing purposes in our case!
