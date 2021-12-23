# Label approved and changes requested pull requests

This GitHub Action applies a label of your choice to pull requests that reach a specified number of approvals or changes requested. For teams using [Pull Reminders](https://pullreminders.com), this action can be used to exclude approved or changes requested pull requests from reminders.

## Usage

This Action subscribes to [Pull request review events](https://developer.github.com/v3/activity/events/types/#pullrequestreviewevent) which fire whenever pull requests are approved or changes requested. The action requires two environment variables – the label name to add and the number of required approvals or changes requested. Optionally you can provide a label name to remove.

```workflow
on: pull_request_review
name: Label approved pull requests
jobs:
  labelWhenApproved:
    name: Label when approved
    runs-on: ubuntu-latest
    steps:
    - name: Label when approved
      uses: pullreminders/label-when-approved-or-changes-requested-action@master
      env:
        APPROVALS: "2"
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        ADD_LABEL: "approved"
        REMOVE_LABEL: "awaiting%20review"
    
    - name: Label when changes requested
      uses: pullreminders/label-when-approved-or-changes-requested-action@master
      env:
        CHANGES_REQUESTED: "1"
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        ADD_LABEL: "changes_requested"
        REMOVE_LABEL: "approved"
```

## Demo

<img src="https://github.com/pullreminders/label-when-approved-action/raw/master/docs/images/example.png" width="540">


## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).
