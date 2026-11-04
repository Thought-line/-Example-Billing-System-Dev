# PulseCheck – Jira OAuth Configuration

## 1. Jira API Permissions

Configured the Jira API permissions in the Atlassian Developer Console.

### Classic Scopes
- `read:jira-work`
- `read:jira-user`
- `manage:jira-webhook`

### Granular Scopes
- `read:issue-details:jira`
- `read:jql:jira`
- `read:board-scope:jira-software`
- `read:sprint:jira-software`
- `read:board-scope.admin:jira-software`

These permissions support:
- Reading Jira projects and issues.
- Fetching user information.
- Accessing boards and sprint details.
- Reading issue details and executing JQL searches.
- Managing Jira webhooks.

## 2. OAuth Callback URL

Configured callback URL in Atlassian Developer Console:

```env
ATLASSIAN_REDIRECT_URI=https://trace-dense-roundness.ngrok-free.dev/api/integrations/jira/callback
```

The callback URL must match the value configured in the backend `.env` file.

## 3. Environment Configuration

Verify the following environment variables:

```env
ATLASSIAN_CLIENT_ID=your_client_id
ATLASSIAN_CLIENT_SECRET=your_client_secret
ATLASSIAN_REDIRECT_URI=https://trace-dense-roundness.ngrok-free.dev/api/integrations/jira/callback
```

**Security:** Never commit the actual Client Secret to GitHub or expose it in frontend code.

## 4. Reconnect Jira in PulseCheck

After saving the Atlassian configuration:

1. Open PulseCheck.
2. Navigate to Integrations.
3. Disconnect the existing Jira connection.
4. Click Connect Jira.
5. Complete the Atlassian OAuth consent process.
6. Verify that the requested permissions are displayed.
7. Confirm that Jira connection is successful.

## 5. Validation

Verify the following after reconnecting:

- Jira projects load successfully.
- Jira issues and assigned users are fetched.
- Boards and sprint information are accessible.
- Story points and board configuration can be retrieved.
- Jira API scope mismatch errors no longer occur.

**Status:** OAuth configuration and callback URL checked. Final validation should be completed after reconnecting Jira and testing the integration.
