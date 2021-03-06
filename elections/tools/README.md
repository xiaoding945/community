
# Election Tools

This directory contains the tools required to generate the kata electorate

## generate_electorate.py

This tool needs the following python libraries:

* pytz
* github3.py
* pyyaml

to install them in a virtual environment do something like:

```bash
$ python3 -m venv .venv
$ .venv/bin/pip install pytz github3.py pyyaml
```

Before running the tool you will need to create a
[GitHub API token](https://github.blog/2013-05-16-personal-api-tokens/)

replace ``__API_TOKEN__`` with your personal token.

Also update the election start and end times.  Then run the tool with:
``$ .venv/bin/python ./generate_electorate.py``

The code looks at all commits in all kata-containers repos *except*
kata-containers/linux and kata-containers/qemu.  As both of these are forks
(in the GitHub sense) they'll have lots of contributors that may not be kata
contributors.

For contributors that have more than one email address it picks one as default
but supplies all the others so  we can be smarter about where to send the
emails.

The sources for email addresses are:
* GitHub account
* Git commit data
* Look for a 'Signed-Off-By' line in the commit message
The GitHub login is always stored so that is the primary identifier.
