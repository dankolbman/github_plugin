# Github Plugin
This plugin moves data from the Github API to S3 or Google Cloud Storage based on the specified object.

## Hooks
### GithubHook
This hook handles the authentication and request to Github. This extends the HttpHook.

### S3Hook
Core Airflow S3Hook with the standard boto dependency.

## Operators
### GithubtoCloudStorageOperator
This operator composes the logic for this plugin. It fetches the Github specified object and saves the result in GCS or S3. The parameters it can accept include the following:
```
:param github_conn_id:           The Github connection id.
:type github_conn_id:            string
:param github_org:               The Github organization.
:type github_org:                string
:param github_repo:              The Github repository. Required for
                                 commits, commit_comments, issue_comments,
                                 and issues objects.
:type github_repo:               string
:param github_object:            The desired Github object. The currently
                                 supported values are:
                                    - commits
                                    - commit_comments
                                    - issue_comments
                                    - issues
                                    - members
                                    - organizations
                                    - pull_requests
                                    - repositories
:type github_object:             string
:param payload:                  The associated github parameters to
                                 pass into the object request as
                                 keyword arguments.
:type payload:                   dict
:param destination:              The final destination where the data
                                 should be stored. Possible values include:
                                    - GCS
                                    - S3
:type destination:               string
:param dest_conn_id:             The destination connection id.
:type dest_conn_id:              string
:param bucket:                   The bucket to be used to store the data.
:type bucket:                    string
:param key:                      The filename to be used to store the data.
:type key:                       string
```
