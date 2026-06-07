1. App Roles (Authorization for Users & Apps)
App Roles define what a user or application is allowed to do inside your API.

🔑 Key Points
Defined under Expose an API

Assigned to users, groups, or service principals

Appear in the token as:
"roles": ["HR"]

Used for authorization, not authentication

Checked by your API backend

2. App Rights (Application Permissions)
App Rights = Application Permissions  
Used when no user is present (daemon apps, background jobs).
Key Points
Require admin consent

Appear in the token as:
"roles": ["User.Read.All"]
Used for server-to-server communication

3. Scopes (Delegated Permissions)
Scopes define what the app can do on behalf of the signed-in user.

🔑 Key Points
Appear in the token as:"scp": "Course.Read"

Used when a user is logged in

Must be defined under Expose an API

Must be consented by the user or admin