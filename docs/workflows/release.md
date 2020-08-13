# WPVIP Website Code Release Procedure

## Important notes
- If the branch/environment exists, always do a pre-release into `preprod`.
- Make sure releases/merges to `preprod` and `master` are of the "merge commit" type.
	- The green button for merging the PR will be labeled "Merge pull request" and in the drop down it is named "Create a merge commit".
- Feature merges into `develop` should be merged in the rebase method where the green button will be labeled "Rebase and merge".
	- This is done so that `develop` has all our features' commits and the commits in `master` + `preprod` stay as clean as possible.

## Defining the changelog
- There should be a Release template for the merge description under `~/.github/PULL_REQUEST_TEMPLATE/release_template.md`
- Gather the Pull Requests(PRs) that were merged into `develop` since the last release (i.e. those that have the HEAD as `develop`), using your preferred method. Options, but not limited to:
	- Using GitHub CLI.
		- `gh pr list --state closed` (at time of publishing) will list most of the information needed.
	- Manually through GitHub UI.
		- Under the repo URL `{repo-url}/pulls?q=is%3Apr+is%3Aclosed` collect the #, title, and note what it affected (theme, plugin, workflow, etc) to match with the Release PR template.
- Make sure to exclude any PRs that were merged into `master` already or those that went to `preprod` since they are likely testing or QA things that should not be in the release notes/changelog.
- Place the PR messages into the corresponding section of the Release Template.
- If applicable, add mentions or closing keywords for issues for each PR message.
- Release names can be found/saved in the site's corresponding sheet in the team's [Google Sheet](https://docs.google.com/spreadsheets/d/19Y3imaw_jkhg2IKVWzxl7G-3eZUpxMWwxSdikmEUcX8/edit#gid=0).

## Release steps
- First do a `vX.XX.XX pre-release` PR from `develop` to `preprod` so the environments stay in sync and let any CI tests complete.
	- Assign yourself to the PR.
- After the above, do a PR from `develop` to `master` with the release number `vX.XX.XX`.
	- Again, assign yourself to the PR.
- If applicable, monitor the CI dashboard for completion.
- Run any post-launch tests.
	- Confirm that features in the release are working either manually or through any CI processes.
	- If the site includes an `info` subdomain, or marketing landing pages, there should be a Cypress testing workflow in the team's [form-tests repo](https://github.com/NationalUniversitySystem/form-tests). Run the reports generator script for the corresponding site and save the files to Google Drive.
- Tag the release under `/releases`
	- Use the same release notes as the PR into `master` branch.
	- Major and Minor releases get names (v1.XX.XX and v1.1.XX) but not patch releases (vX.X.1).
- If accessible, add an annotation of the release and version number to Google Analytics.

## Housekeeping
- Clean unused and already merged `branches`. Make sure you exercise good housekeeping by deleting unused branches locally and remotely.
- Close `issues`. Make sure you close those issues that have been fixed, in case they were not automatically closed via keywords in the release notes.
