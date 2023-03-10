---
title: "Documenting progress of examining os packages version tracking"
excerpt: "Documenting progress of examining os packages version tracking"
publishDate: "2023-03-10T19:58:36.050Z"
image: "https://learn.g2.com/hubfs/G2CM_GI129_Glossary_Article_Images-%5BOnline_Behavior_Tracking%5D_V1b.png"
category: "Docs"
author: "Abdelfattah Hilmi"
layout: "@layouts/BlogLayout.astro"
tags: [Cloud, Devsecops, SRE]
---

## Tracking tools:

- Repology: https://repology.org/
- pkgs.org: https://pkgs.org/
- openhub: https://www.openhub.net

---

## Repology Api

#### Endpoint : https://repology.org/api/v1/
<b>How to get data related to a project across distros</b>
by default the api returns the first 200 metions of the project searched this example prints the first 10 :

```python
import requests

url = "https://repology.org/api/v1/project/firefox"

response = requests.request("GET", url)
print(response.json()[:10])
```
The API returns:

```json
[
	{
		"repo": "archlinux32_i486",
		"subrepo": "extra",
		"srcname": "firefox-i18n",
		"binname": "firefox-i18n-is",
		"visiblename": "firefox-i18n-is",
		"version": "108.0.2",
		"licenses": [
			"MPL",
			"GPL",
			"LGPL"
		],
		"summary": "Icelandic language pack for Firefox",
		"status": "outdated",
		"origversion": "108.0.2-1.0"
	},
	{
		"repo": "archlinux32_i486",
		"subrepo": "extra",
		"srcname": "firefox-i18n",
		"binname": "firefox-i18n-zh-cn",
		"visiblename": "firefox-i18n-zh-cn",
		"version": "108.0.2",
		"licenses": [
			"MPL",
			"GPL",
			"LGPL"
		],
		"summary": "Chinese (Simplified) language pack for Firefox",
		"status": "outdated",
		"origversion": "108.0.2-1.0"
	},
	{
		"repo": "arch",
		"subrepo": "extra",
		"srcname": "firefox-i18n",
		"binname": "firefox-i18n-da",
		"visiblename": "firefox-i18n-da",
		"version": "110.0.1",
		"licenses": [
			"MPL",
			"GPL",
			"LGPL"
		],
		"summary": "Danish language pack for Firefox",
		"status": "newest",
		"origversion": "110.0.1-1"
	},

    ...]

```

<b>How to Filter data using url query parameters</b>

filters are :<br/>
<b>search:</b> project name substring to look for <br/>
<b>maintainer:</b> return projects maintainer by specified person<br/>
<b>category:</b> return projects with specified category<br/>
<b>inrepo:</b> return projects present in specified repository<br/>
<b>notinrepo:</b> return projects absent in specified repository<br/>
<b>repos:</b> return projects present in specified number of repositories (exact values and open/closed ranges are allowed, e.g. 1, 5-, -5, 2-7)<br/>
<b>families:</b> return projects present in specified number of repository families (for instance, use 1 to get unique projects)<br/>
<b>repos_newest:</b> return projects which are up to date in specified number of repositories<br/>
<b>families_newest:</b> return projects which are up to date in specified number of repository families<br/>
<b>newest:</b> return newest projects only<br/>
<b>outdated:</b> return outdated projects only<br/>
<b>problematic:</b> return problematic projects only<br/>


Example: get the newest version of every package which has a name with `python3` as a substring in the repo ubuntu_22_04 (theoritically, but the API returns all repos of debian based distros)

```python
import requests

url = "https://repology.org/api/v1/projects/?search=python3&inrepo=ubuntu_22_04&newest=1"

response = requests.request("GET", url)
print(response.json())
```

the API returns: 

```json
{
	"python3-antlr4": [
		{
			"repo": "pardus_21",
			"subrepo": "main",
			"srcname": "python3-antlr4",
			"visiblename": "python3-antlr4",
			"version": "4.9.1",
			"maintainers": [
				"team+python@tracker.debian.org",
				"crusoe@debian.org"
			],
			"categories": [
				"misc"
			],
			"status": "unique",
			"origversion": "4.9.1-1"
		},
		{
			"repo": "parrot",
			"subrepo": "parrot-updates/main",
			"srcname": "python3-antlr4",
			"visiblename": "python3-antlr4",
			"version": "4.9.1",
			"maintainers": [
				"team+python@tracker.debian.org",
				"crusoe@debian.org"
			],
			"categories": [
				"misc"
			],
			"status": "unique",
			"origversion": "4.9.1-1"
		},
        ...]
```

## pkgs.org Api
API is not free !!!
we need to scrape serch results if possible (they have captcha)

## openHub
presents valuable insights about package maintainace, Activity, vulns+sast report, contributors ... but does not specify releases/versions 

---
## Other tools I'm checking:

- https://pypi.org/project/nvchecker/