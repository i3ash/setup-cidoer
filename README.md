# setup-cidoer

[CIDoer](https://github.com/i3ash/cidoer) is a unified Bash scripting framework that integrates seamlessly with multiple CI/CD workflows.

`setup-cidoer` simplifies CIDoer integration to Github Actions.

## Features

+ Unified Framework: Consistent Bash-based scripting across multi CI/CD platforms.
+ Automatic Setup: Downloads and configures the CIDoer environment.
+ Flexible Integration: Compatible with various CI/CD services.
+ Extensible: Utilize cidoer.core.sh for advanced Bash scripting.

## Usage

Add CIDoer action steps to your GitHub Actions workflow:
```Yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup CIDoer
        uses: i3ash/setup-cidoer@v1
      - name: Run CIDoer Script
        shell: bash
        run: |
          source "${CIDOER_CORE_FILE:?}"
          do_print_dash_pair 'GITHUB_RUN_NUMBER' "${{ github.run_number }}"
          do_workflow_job build
          do_workflow_job upload
```

### Action Inputs

| Input     | Description                                  | Default | Required |
|-----------|----------------------------------------------|---------|----------|
| ref       | Git reference to download (branch, tag, SHA) | main    | No       |
| directory | Destination directory for the source code    | .cidoer | No       |

### Action Outputs

None currently. Future updates may include outputs.

## Support

For issues or questions, open an issue on the GitHub repository.

## License

This project is licensed under the MIT License.
