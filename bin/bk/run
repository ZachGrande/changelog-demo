#!/bin/bash -e
# BRANCH=$(git rev-parse --abbrev-ref HEAD)
# COMMIT=$(git rev-parse HEAD)

if ! command -v jq &> /dev/null
then
  echo "Please install jq: https://jqlang.github.io/jq/download/"
  exit 1
fi
# NOTE: using jq to escape the message for JSON
# MESSAGE=$(git log -1 --pretty=%B | jq -Rsa .)

# if [ -z "$BRANCH" ] || [ -z "$COMMIT" ] || [ -z "$MESSAGE" ]; then
#   echo "Error: BRANCH, COMMIT, or MESSAGE is empty. Please ensure you are in a valid git repository."
#   exit 1
# fi

# if ! git diff --quiet origin/$BRANCH $BRANCH; then
#   echo "There are some local commits that need to be pushed to the remote. Please push your changes before proceeding."
#   exit 1
# fi

if ! command -v bk &> /dev/null
then
  echo "Buildkite CLI could not be found. Please follow this guide to configure the CLI:"
  echo ""
  echo "#### Install the CLI ####"
  echo "* MacOS installation: brew install buildkite/buildkite/bk@3"
  echo "* Windows installation: Download the latest release and run bk.exe: https://github.com/buildkite/cli/releases"
  echo "* More info: https://buildkite.com/docs/cli/installation"
  echo ""
  echo "#### Authenticate the CLI ####"
  echo "* Visit this link in your browser:"
  echo ""
  echo "https://buildkite.com/user/api-access-tokens/new?description=Buildkite%20CLI&scopes%5B%5D=read_agents&scopes%5B%5D=write_agents&scopes%5B%5D=read_clusters&scopes%5B%5D=write_clusters&scopes%5B%5D=read_teams&scopes%5B%5D=write_teams&scopes%5B%5D=read_artifacts&scopes%5B%5D=write_artifacts&scopes%5B%5D=read_builds&scopes%5B%5D=write_builds&scopes%5B%5D=read_build_logs&scopes%5B%5D=read_organizations&scopes%5B%5D=read_pipelines&scopes%5B%5D=write_pipelines&scopes%5B%5D=read_user&scopes%5B%5D=read_suites&scopes%5B%5D=write_suites&scopes%5B%5D=read_registries&scopes%5B%5D=write_registries&scopes%5B%5D=delete_registries&scopes%5B%5D=read_packages&scopes%5B%5D=write_packages&scopes%5B%5D=delete_packages&scopes%5B%5D=graphql"
  echo ""
  echo "* Organization ID: recognize-1"
  echo "* Copy the resulting API token to your clipboard"
  echo "* Run 'bk configure' and paste the API token when prompted"
  echo "* Once complete, run 'bk use' and select 'recognize-1'
  echo "* More info: https://buildkite.com/docs/cli/configuration"
  echo ""
  echo "#### Sanity Check ####"
  echo "Run 'bk pipeline view' to get pipeline details. This will fail if the CLI is not configured correctly."
  echo ""
  echo "Full Recognize wiki: https://github.com/Recognize/recognize/wiki/%5BWIP%5D-CI:-Buildkite"
  exit 1
fi

response=$(bk api --method GET /builds)

echo $response

echo "Response from Buildkite API above!"
