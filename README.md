# Software Engineering Group 5

Jacob Alongi, Matt Hudson, Tim Kuehner, Rebecca Parker

**Sprint 1** [here](./sprint-1)

**Sprint 2** [here](./sprint-2)

**Sprint 3** [here](./sprint-3)

# Sprint 4 README

## Deployment Instructions

## Files/Code Modified

## Completeness

Our project relies on the augur database running on the same server that runs Augur's backend server. It does not rely on endpoints outside the normal Augur environment. You could point Augur to augur's database if you want; it *should* work, because we did not edit anything regarding that configuration - we just added endpoints that access the database in the same
way every other endpoint accesses the database.

## Testing

We modeled the tests for our 3 new endpoints after the existing Augur testing design for consistency. First, we created functional tests to ensure that the function will actually execute. We first mocked the metrics model and then called the new functions to test that some values were returned. 
```python
def test_repo_timeline(metrics):
    assert metrics.repo_timeline(20, 21000).iloc[0].net > 0
```

In addition, we tested the routes on the live development server to ensure that the function executes on the live server as well, returning non-empty data.
```python
def test_repo_timeline(metrics):
    response = requests.get('http://localhost:5000/api/unstable/repo-groups/20/repos/21000/repo-timeline')
    data = response.json()
    assert response.status_code == 200
    assert len(data) >= 1
    assert data[0]["net"] > 0
```
## Release

## Science Fair (in-class demopalooza)

For our demonstration, we demonstrated our endpoints running with various repos and repo groups. We used the augur repository and repogroup to demonstrate endpoints 1 and 2, and we used Dr. Goggins (s@goggins.com) as our example for Endpoint 3. We also demonstrated the incredible power of the `sl` bash command. a.k.a if you mistype the `ls` command. It's less of a trainwreck than my finals next week.

## Feedback Incorporation

We found the endpoints to be satisfactory as they were presented in Sprints 2 and 3, as do you:

> Good progress for sprint 2!

> Sean Goggins, Nov 30 at 6:45am

> Really great progress on the endpoints!

> Sean Goggins, Dec 1 at 2:15pm

:)

But seriously, we didn't find any feedback issues, so we focused on the demo and this README.

-------------------------------------
Base Augur Readme Below

-------------------------------------
# Augur

branch | status
   --- | ---
master | [![Build Status](https://travis-ci.org/chaoss/augur.svg?branch=master)](https://travis-ci.org/chaoss/augur)
   dev | [![Build Status](https://travis-ci.org/chaoss/augur.svg?branch=dev)](https://travis-ci.org/chaoss/augur)

[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/2788/badge)](https://bestpractices.coreinfrastructure.org/projects/2788)

## About Augur

Augur is focused on prototyping open source software metrics.

Functionally, Augur is a prototyped implementation of the Linux Foundation's [CHAOSS Project](http://chaoss.community) on [open source software metrics](https://github.com/chaoss/metrics). Technically, Augur is a [Flask web application](http://augur.osshealth.io), [Python library](https://oss-augur.readthedocs.io/en/dev/library-documentation/python.html) and [REST server](http://augur.osshealth.io/static/api_docs/) that presents metrics on open source software development project health and sustainability.

## Getting Started

**Please follow the 'Getting Started' guide in our [documentation](https://oss-augur.readthedocs.io/en/master/getting-started/getting-started-toc.html).**

Note: we currently only support (most) UNIX systems. If you would like to use Augur but only have access to a non-Unix system, we recommend setting up an Ubuntu 18.04 VM if you can. 
If this is not feasible for you, please reach out to us at [p9j0r6s0m4a0t8v5@augurlabs.slack.com](mailto:p9j0r6s0m4a0t8v5@augurlabs.slack.com) and we will try to help you come up with a solution. In the meantime, if you have Windows and feel so inclined check out issue [#403](https://github.com/chaoss/augur/issues/403) as a starting point until we can finalize a Windows installation.

## Data Collection

Please [follow the instructions](https://oss-augur.readthedocs.io/en/master/getting-started/usage.html#db) for collecting data about specific repositories of interest. We are also currently working on putting together an easily distributable sample database to enable people to get going faster.

<!-- TODO: link to worker docs once they're done -->
<!-- If you are collecting data of your own, you must [start up the workers](./docs/setup/augur-get-workers-going.md). -->

If you have any issues, please feel free to request to email straight into our slack channel [p9j0r6s0m4a0t8v5@augurlabs.slack.com](mailto:p9j0r6s0m4a0t8v5@augurlabs.slack.com) for new developer support!!

## Contributing
----------------

To contribute to Augur, please follow the guidelines found in our [CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md). Augur is a welcoming development community that is open to anyone and everyone of every skill level!

Check out our [documentation](https://oss-augur.readthedocs.io/en/documentation/) for information about our system.

Please note we require all commits to be signed off with a [Developer Certificate of Origin](https://developercertificate.org/) in accordance with the [CHAOSS Project Charter section 8.2.1](https://chaoss.community/about/charter/#user-content-8-intellectual-property-policy). This can be easily done by using the `-s` flag when using `git commit`, e.g. `git commit -s -m "Update README.md"`. **Any pull request containing commits that are not signed off will not be eligible for merge until all commits are signed off.** 

## License, Copyright, and Funding
----------------

Copyright © 2019 University of Nebraska at Omaha, University of Missouri and CHAOSS Project at the Linux Foundation

Augur is free software: you can redistribute it and/or modify it under the terms of the MIT License as published by the Open Source Initiative. See the [LICENSE](LICENSE) file for more details.

This work has been funded through the Alfred P. Sloan Foundation.
