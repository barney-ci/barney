# barney

Barney is an Arista Networks project that manages dependencies across
builds involving multiple repositories, caching all build artifacts so
they may be re-used across builds.  You can think of barney as
providing capabilities similar to what you get with the go toolchain,
but generalized for a mixed-language environment.

For now, Barney is Arista proprietary, and this repo is just a
redirector to enable "go get" to work on "barney.ci/barney" within
Arista's VPN, which is needed to make Go modules work properly with
imports of "barney.ci/barney".

## Note to Barney Maintainers

The way this works is:

  1. We've set up barney.ci's DNS to return github A-records for barney.ci.

  2. "barney.ci" is configured as the "URL" of the github "barney-ci" organization.

  3. We've added a "gh-pages" branch to this repository and turned on
     "GitHub pages" to serve that branch via http.

  4. Now, when an http client fetches "https://barney.ci/barney", DNS
     directs you to github (thanks to step 1), which maps the URL to
     "github.com/barney-ci/barney" (thanks to step 2), and returns
     content from the gh-pages branch of this repository (thanks to
     step 3).

Someday, if we decide to open source barney, we may move the code
itself to the "main" branch here.

    -kduda 2021-02-10
