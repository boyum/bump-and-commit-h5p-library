# bump-and-commit-h5p-library

A composite action that combines commit and bump-h5p-library actions.

Update the library version by commenting either `/bump major`, `/bump minor`, or `/bump patch` in a Pull Request. If major or minor is updated, any below version type will be set to 0, e.g. if minor version is bumped, patch will be set to 0.

This action pairs well with [boyum/is-h5p-library-updated-action](https://github.com/boyum/is-h5p-library-updated-action).

⚠️ If you want the commit that this action pushes to trigger a new workflow run, you need to create your own [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

## Usage

This action needs to be triggered by `issue_comment`, as such:

```yml
on: [issue_comment]

jobs:
  bump-library:
    name: Bump library version

    runs-on: ubuntu-latest

    steps:
      - name: Bump and commit library
        uses: boyum/bump-and-commit-h5p-library@latest
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

### Options

| Name                | Required | Default value | Description                                                                        |
| ------------------- | -------- | ------------- | ---------------------------------------------------------------------------------- |
| `github-token`      | true     | -             | A GitHub Token or a Personal Access Token.                                         |
| `working-directory` | false    | `.`           | The directory where the library.json file is located, relative to the Git project. |
