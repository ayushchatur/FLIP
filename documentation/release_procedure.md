# Table of Contents

- [Executive Summary](#executive-summary)
- [Document Purpose](#document-purpose)
- [Change Types](#change-types)
  - [Production](#production)
    - [Planned Releases](#planned-releases)
    - [Unplanned (Hotfix) Releases](#unplanned-hotfix-releases)
    - [Hotfix Process](#hotfix-process)
    - [Third Party Changes](#third-party-changes)
  - [UAT](#uat)
    - [Iterative Releases](#iterative-releases)
- [Production Trust Access](#production-trust-access)
- [Supporting Documentation](#supporting-documentation)
  - [Release Notes](#release-notes)
  - [Systems Documentation](#systems-documentation)
    - [Clinical Safety](#clinical-safety)
    - [Information Governance](#information-governance)
    - [Training](#training)
    - [Test Evidence](#test-evidence)
  - [Root Cause Analysis](#root-cause-analysis)
- [Release Testing](#release-testing)
  - [SIT Process](#sit-process)
  - [UAT Process](#uat-process)
  - [Production Smoke Test](#production-smoke-test)
- [Feature Flags](#feature-flags)
- [Environments](#environments)
- [RACI](#raci)

# Executive Summary

Answer Digital will manage releases to all environments including Production. The Production release cadence will directly align with the product roadmaps giving clear visibility when a new version will be available to the Trusts. Early sight of production releases will enable Trusts to plan accordingly and for system documentation to be updated. 

In addition to planned production releases, features will be deployed to UAT for iterative user testing, feedback and sign off. 

A shared cloud pre-prod environment will mirror the FLIP version deployed to production. This environment mimics two Trusts with both FLIP and AIDE running on the same hardware so that any compatibility issues can be identified between new versions of AIDE and FLIP before production. Cloud pre-prod will also be used for demo and training purposes and provide an environment for testing unplanned bug fixes. UAT will be used for testing new features iteratively.

FLIP production releases will be subject to downtime. Trusts will be notified of downtime and when the system is fully restored. The central FLIP UI will display a banner explaining any downtime and when the system is predicted to be back online. Release notes will accompany any release and training documentation will be created iteratively.

# Document Purpose

This page details the ongoing release process that FLIP will follow covering planned and unplanned release procedures, change types and cadence and supporting documentation.

# Change Types

## Production

### Planned Releases

Planned production releases are aligned to the FLIP product roadmap in order to deliver valuable scheduled updates to the Trusts. Planned production releases will:

- Contain new features, enhancements and fixes to bug tickets.
- Will be made up of 1 or more features.
- Release schedules will be shared with the consortium Trusts and AI Centre.
- Releases will be created in Jira including all tickets for the Planned production release so the entire scope of change can be viewed.
- Full release notes will be published prior to a production release.
- All UAT activities must be fully complete prior to a release with Product Owner sign off.
- Release will take place at a time that will keep user impact to a minimum. Exact times will be arranged closer to the time of release subject to availability.

### Unplanned (Hotfix) Releases

Unplanned or hotfix releases will only be triggered if a production severity 1 (blocker) issue is raised via the service desk.

FLIP will be taken offline and users will be unable to use FLIP if any of the following criteria are met:

- There is any potential risk to other Clinical Systems such as AIDE that requires FLIP to be disabled in order to resolve the issue.
- The bug may cause data in the Application to be at risk of being lost or impacting the system in a way that could further impact FLIP.

### Hotfix Process

- New ad-hoc release will be created in Jira with the severity 1 issue attached.
- Communications notifying the consortium Trusts and AI Centre of the issue will be sent.
- Upon investigation of the issue and depending on the impact and fix lead time, a hotfix release may be deployed to each Trust / Central Hub fixing the bug and restoring BAU.
- The Root Cause Analysis (RCA) document will be updated and shared with the AI Centre for sign off.
- Hotfixes will be deployed and tested on Pre-Prod prior to the production release.

### Third Party Changes

Third party changes include any OS patching or hardware maintenance. These changes will not be undertaken by Answer.  

Prospective dates and change content must be shared with Answer so that impact assessments can be undertaken prior to the change date.

Answer is not responsible for any loss of functionality or services due to 3rd party updates.

## UAT

### Iterative Releases

Iterative UAT releases are aligned to Continuous Deployment best practices and build up functionality which contribute towards the scope of a planned production release. This will include new features, enhancements and bugs. New features and enhancements will be released to the UAT environment to enable iterative user testing and feedback to ensure the right product is being built.

- Versioned releases will be released to UAT when all scoped tickets meet the definition of done
- Training documentation and test evidence will accompany a UAT release.
- A UAT release will be created in Jira with the feature tickets attached.
- Release notes will be published to the Product Owner prior to a UAT release.

## Production Trust Access

Production changes will be deployed remotely using Ansible as the chosen Infrastructure-as-Code (IaC) solution. These will be orchestrated by the Ansible Control Node on the Central Hub network, and be applied to each Trust as remote hosts over the Site-to-Site VPN connections set up as part of the Trust onboarding process.

## Supporting Documentation

### Release Notes

Release notes will be created and distributed alongside a release. They will briefly describe the change and the tickets that are included in a product update (e.g. new features, feature enhancements, or bug fixes).

- Use Jira standard release notes templating for tickets included.
- UAT release notes will be shared with the AI Centre and Product Owner.
- Production release notes will be shared with the AI Centre and Trusts.
- Production release notes will include versions of services to be deployed to production.
- Production release notes will list any known issues which are outstanding at the time of deployment.
- Release notes will be distributed using the release notes template.

## Systems Documentation

### Clinical Safety

Clinical safety documents will be updated when appropriate to do so based on the release content. These documents will be published and shared via the release notes.

### Information Governance

Information Governance documents will be updated when appropriate to do so based on the release content. These documents will be published and shared via the release notes.

### Training

Training documentation will be updated where necessary to accompany a new release and will be shared with Trusts in advance of a new release or Trust onboarding.

### Test Evidence

Evidence gathered throughout SIT will be stored and can be shared via the release notes.

### Root Cause Analysis

RCA (Root Cause Analysis) is a structured process to find the root cause of issues reported in Live post a production deployment. It will be performed on the discovery of any Sev 1 or 2 issues to improve the performance and quality of future releases and give assurances that issues have been remedied effectively.

Issues will be added to the RCA list and shared with the AI Centre and Trusts as required.

## Release Testing

### SIT Process

All releases will go through comprehensive automated and manual functional and non-functional testing before being deployed to UAT. The entire automated and manual system testing processes can be viewed in the [AI Centre Test Strategy](./test_strategy.md).

- SIT evidence will be attached to stories and shared via Jira with Product Owners and UAT Testers.
- Features will not be released to UAT if they do not pass SIT or have outstanding Sev 1 issues.
- Scope and progress of SIT testing can be viewed within Jira via the sprint dashboards and on a Jira Story.
- SIT test evidence will be attached to release notes for reference.

## UAT Process

Manual iterative UAT will be implemented for signing off new features before being released to production.

- Features that require UAT will be identified when agreeing the scope of a Planned production release.
- Existing SIT Test Scripts will be leveraged to train UAT Testers.
- Feedback will be given on a testing Trello board.
- If UAT does not sign off a feature then the Product Owner reserves the right to delay the planned production release.

## Production Smoke Test

Depending on the content of a production release, a production smoke test will be undertaken to validate that the production deployment is successful.

- Smoke test processes are documented in QMetry within Jira and will be shared with the user who will perform the test.
- Production smoke tests for FLIP will be undertaken at a preferred Trust by a member of that particular trust.

## Feature Flags

Feature flags will be implemented where appropriate to enable continuous deployment of features. This will enable Answer to turn off unfinished features which are not appropriate for testing without having long-lived feature branches.

- Feature flags will not be dynamic.
- Feature flags will be global and controlled by Answer meaning all Trusts will have the same functionality available.

## Environments

| Environment | Use | Deployment Criteria |
|-------------|-----|---------------------|
| Dev (Cloud) | A volatile environment that is used by Answer developers. Since much of the architecture is difficult to simulate locally, this ecosystem is required to facilitate development of new functionality. | N/A |
| SIT (Cloud) | A stable environment to enable the testers to assure the quality of the latest release candidates. | - Dev is complete<br/>- Automation tests have passed<br />- Automated regression tests have passed |
| UAT (Cloud) | A stable environment to allow the primary stakeholders, product owners and users to test the latest release candidates. This environment will be running full time to enable iterative user testing and new feature demos. |- SIT has been fully signed off by AD<br />- SIT results shared with PO<br />- Training documentation has been updated and shared<br />- Release notes have been shared with PO |
| Pre-Prod (Cloud) | An environment matching the production hardware as closely as possible, allowing AIDE and FLIP to be tested on the same infrastructure. This environment will be running full time to emulate the production environment. Environment will also be used for training and platform demo purposes. | - UAT has been fully signed off by PO<br />- Full production release notes have been shared with all stakeholders |
| Production (All Trusts) | An  environment within each Trust running FLIP, potentially also AIDE | - OAT has been fully signed off<br />- Release dates have been shared by AD and agreed with the Trust<br />- Any required NFR testing has passed |

## RACI

| Task | Answer Dev Team | Product Owner | AI Centre | UAT Testers | Trusts |
|------|-----------------|---------------|-----------|-------------|--------|
| Defining the scope of a planned release | R | A | - | - | - |
| Planning and sharing planned release schedule | AR | C | I | - | CI |
| Creating and closing releases in Jira | AR | I | I | - | - |
| Creating and  distributing release notes | AR | I | I | - | I |
| Training and UAT handover documentation | AR | C | - | CI | - |
| Communicating Unplanned fix dates | AR | C | C | - | C |
| Deploying to SIT, UAT,  Pre Prod and Production | AR | I | I | I | I |
| AIDE Production smoke test | A | I | I | - | R |
| FLIP Production smoke test | AR | I | I | - | I |
| Performing UAT testing | A | I | - | R | - |
| Signing off features | A | R | - | C | - |
| Signing off a production release  candidate | A | R | I | - | I |

A - the person who is accountable for the success of the task and is the decision-maker.

R - The person who is responsible for doing the work.

C - The person or group who need to be consulted for details and additional info on requirements

I - The person or group who needs to be kept informed of major updates# Table of Contents
