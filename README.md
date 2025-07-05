# On-Demand Admin Access

On-Demand Admin Access is a custom application for ServiceNow that enables secure, temporary administrative access for users as needed. This solution is designed to help organizations manage privileged access more efficiently, reducing security risks and maintaining compliance.

## Features

- **Grant Temporary Admin Access:** Easily provide users with admin privileges for a limited time.
- **Audit and Compliance:** Track and log all admin access requests and activities for compliance reporting.
- **Customizable Workflows:** Integrate approval processes, notifications, and automation as needed.
- **ServiceNow Native:** Built as a scoped application for seamless integration with the ServiceNow platform.

## Getting Started

### Prerequisites

- A ServiceNow instance (Rome, San Diego, or later recommended)
- Admin access to your ServiceNow environment

### How to Import Application

I had been beating my head for over a week on how to import my application from GitHub to my PDI.

Finally fixed the issue by following the below steps:

**On your GitHub account:**

1. Log in to your GitHub account.
2. Navigate to [Personal Access Tokens](https://github.com/settings/tokens/new).
3. Create a new token by selecting all the options for the scopes.
4. Click on "Generate token".

**On your PDI (Personal Developer Instance):**

1. Navigate to `https://xxxxx.service-now.com/discovery_credentials_list.do?sysparm_query=&sysparm_view=`
2. Click on "New".
3. Select the connection type as **Basic Auth Credentials**.
4. Give a name to the connection.
5. Under username, enter your GitHub username.
6. Under password, provide the token created above in GitHub.

**On App Engine Studio:**

1. Click on **Import App**.
2. Under URL, provide the repository link to GitHub.
3. Under branch, put `master`.
4. Under credentials, use the credential created in your PDI instance above.

> For a detailed step-by-step guide, refer to the [ServiceNow DevOps Forum Post](https://www.servicenow.com/community/devops-forum/connect-your-pdi-to-github-to-import-application/td-p/2363339).

### Mandatory Steps to Perform Post Import

- Upload and commit `Jaineel_Call_Lockout (sys_remote_update_set_15755820833866104cd2c900feaad3cf).xml`
- Open the `sys_db_object` record for `sys_user_has_role` and set **"Can Delete"** to `true`

### Optional Steps to Perform

- If you want to enable flow reporting, update the `com.snc.process_flow.reporting.level` property to `FULL`.

### Additional Configuration

- Update the `sn_source_control.properties` file as needed for your environment.
- Set up approval workflows, notifications, and admin access duration according to your policy.

## Usage

1. **Request Admin Access:** Users submit a request using the ServiceNow interface.
2. **Approval Workflow:** The request goes through a customizable approval process.
3. **Grant Access:** Upon approval, admin rights are granted for the specified duration.
4. **Revoke Access:** Admin rights are automatically revoked after the time window, or manually by an admin.

## Repository Structure

- `Jaineel_Call_Lockout (sys_remote_update_set_15755820833866104cd2c900feaad3cf).xml` — update set contains script include which is used in on-Demand Admin Access module to forceLogoutUser.
- `sn_source_control.properties` — Source control properties for ServiceNow integration
- `LICENSE` — License information

## License

This project is licensed under the terms described in the [LICENSE](LICENSE) file.

## Contributing

Contributions, issues, and feature requests are welcome! Please open an issue to discuss your ideas or report bugs.

## Contact

Created by [ImJaineel](https://github.com/ImJaineel).
