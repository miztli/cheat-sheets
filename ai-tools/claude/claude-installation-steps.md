1. Download google-cloud-cli-darwin-arm.tar.gz from https://cloud.google.com/sdk/docs/install
2. Extract the archive: tar -xf google-cloud-cli-darwin-arm.tar.gz
3. Upgrade python3 to 3.10 and up: The gcp installer upgraded python at the end of the installation to Python 3.13.7
4. Authenticate client:
  1. $ gcloud auth application-default login --no-browser
  2. open a new tab and type: $ gcloud auth application-default login --remote-bootstrap="https://accounts.google.com/o/oauth2/auth?response_type=code&client_id=764086051850-6qr4p6gpi6hn506pt8ejuq83di341hur.apps.googleusercontent.com&scope=openid+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloud-platform+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fsqlservice.login&state=dmS9cjOHG6tEzned6Ma78AtSjnvl2S&access_type=offline&code_challenge=RBeZGuNsbL5s3M26aMxgPm2P_lBa7rIym94MbJMyHL8&code_challenge_method=S256&token_usage=remote"
  3. Copy the output command into step #1
  4. Credentials should be saved to file: Credentials saved to file: [/Users/emelgoza/.config/gcloud/application_default_credentials.json]
  5. List stored credentials: $ cat /Users/emelgoza/.config/gcloud/application_default_credentials.json
  6. Set quota project after getting message (WARNING: Your active project does not match the quota project in your local Application Default Credentials file. This might result in unexpected quota issues.):
      $ gcloud auth application-default set-quota-project sep-devqa-digital-ai
5. The Claude CLI needs to be explicitly configured to use Vertex AI instead of its default direct API. This is done using environment variables.
   Set the environment variables: Add the following lines to your shell profile file (For Linux, Mac: ~/.zshrc, ~/.bashrc; For Windows: Adjust user environment variables ) to make the settings persistent across terminal sessions.
    export CLAUDE_CODE_USE_VERTEX=1 # This flag tells the CLI to use Vertex AI for all API requests.
    export CLOUD_ML_REGION=global # This sets the region for your requests. You can change this to a specific region if needed.
    export ANTHROPIC_VERTEX_PROJECT_ID=sep-devqa-digital-ai # Specifies the GCP project to which the API requests will be billed.
    export GOOGLE_APPLICATION_CREDENTIALS=$HOME/.config/gcloud/application_default_credentials.json
6. Install claude CLI: $ npm install -g @anthropic-ai/claude-code
7. Remove old API tokens:
  $ rm ~/.claude.json
  $ rm ~/.claude/settings.json
8. Position in a code directory and launch claude: $ claude
9. Init claude project: $ /init

Notes:
To list installed components:
  $ gcloud components list

To install or remove components at your current Google Cloud CLI version [548.0.0], run:
  $ gcloud components install COMPONENT_ID
  $ gcloud components remove COMPONENT_ID

To update your Google Cloud CLI installation to the latest version [548.0.0], run:
  $ gcloud components update

List google claude version
  $ gcloud --version

Test:
- Ask claude: Provide a brief summary of what this project is about.

References:
- https://confluence.sephora.com/wiki/spaces/CLDENG/pages/548110400/Using+GCP+Vertex+AI+for+Claude+Code+login
- https://cloud.google.com/sdk/docs/install