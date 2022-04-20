# bump-and-commit-h5p-library

A composite action that combines commit and bump-h5p-library actions

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
