| Input              | Required | Default                             | Description                                                                                                                                                                                                                                                                                                              |
| ------------------ | -------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ssh_key            | yes      |                                     | SSH public key.                                                                                                                                                                                                                                                                                                          |
| access_token       |          |                                     | Personal access token with `repo` permissions. Always required on *destination*. Required on *SoT* only if the variable `sot_branch` below is left empty and to decide between **push** and **init** workflows.                                                                                                          |
| sot_repo           |          |                                     | Source repository (Source of Truth).                                                                                                                                                                                                                                                                                     |
| sot_branch         |          |                                     | SoT branch. Defaults to your repository's default branch.                                                                                                                                                                                                                                                                |
| destination_repo   |          |                                     | Destination repository.                                                                                                                                                                                                                                                                                                  |
| destination_branch |          |                                     | Destination branch. Defaults to the same as your SoT's branch name.                                                                                                                                                                                                                                                      |
| push_include       |          | **                                  | Files to include when pushing from SoT => Destination (space separated globs). Defaults to all files.                                                                                                                                                                                                                    |
| push_exclude       |          |                                     | Files to exclude when pushing from SoT => Destination (space separated globs). Defaults to none.                                                                                                                                                                                                                         |
| push_move          |          |                                     | Files to move before pushing from SoT => Destination. In the format `from\|\|to\|\|match` where `match` is a glob filter to match only specific files within `from` (defaults to all). Separate each move operation by a line return. Defaults to reverse of `pr_move`. `push_move` is always run before `push_replace`. |
| push_replace       |          |                                     | Files to replace before pushing from SoT => Destination. In the format `search\|\|replace\|\|match` where `match` is a glob filter to search only those files (defaults to all). Separate each replace operation by a line return. Defaults to reverse of `pr_replace`. `push_replace` is always run after `push_move`.  |
| pr_include         |          | **                                  | Files to include when pulling from Destination => SoT (space separated globs). Defaults to all files.                                                                                                                                                                                                                    |
| pr_exclude         |          |                                     | Files to exclude when pulling from Destination => SoT (space separated globs). Defaults to none.                                                                                                                                                                                                                         |
| pr_move            |          |                                     | Files to move before pushing from Destionation => SoT. In the format `from\|\|to\|\|match` where `match` is a glob filter to match only specific files within `from` (defaults to all). Separate each move operation by a line return. Defaults to none. `pr_move` is always run after `pr_replace`.                     |
| pr_replace         |          |                                     | Files to replace before pushing from Destionation => SoT. In the format `search\|\|replace\|\|match` where `match` is a glob filter to search only those files (defaults to all). Separate each replace operation by a line return. Defaults to none. `pr_replace` is always run before `pr_move`.                       |
| committer          |          | Github Actions <actions@github.com> | Who will commit changes.                                                                                                                                                                                                                                                                                                 |
| custom_config      |          |                                     | Copybara custom configuration file to use. Using this will ignore all the pr_* and push_* inputs.                                                                                                                                                                                                                        |
| workflow           |          |                                     | Workflow to execute. Defaults to auto-detect (init / push / pr).                                                                                                                                                                                                                                                         |
| copybara_options   |          |                                     | Use this, if you want to manually specify some command line options (space-separated).                                                                                                                                                                                                                                   |
| ssh_known_hosts    |          |                                     | SSH known hosts file contents, for authenticating with Copybara with another Git server. GitHub is always included by default.                                                                                                                                                                                           |
| copybara_image     |          | olivr/copybara                      | Copybara Docker image to run.                                                                                                                                                                                                                                                                                            |
| copybara_image_tag |          | latest                              | Copybara Docker image tag to use.                                                                                                                                                                                                                                                                                        |
| pr_number          |          |                                     | If you manually specified the 'pr' workflow, you will need to specify the PR number as well.                                                                                                                                                                                                                             |
| create_repo        |          | yes                                 | If the destination repo doesn't exist, it will be created (subject to enough permissions attached to the access token).                                                                                                                                                                                                  |