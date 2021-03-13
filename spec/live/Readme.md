 - Make an empty account (company name Z3N, email <something>@zendesk.com, so it can be filtered)
 - Create an Admin user (ownwer cannot verify user identities) and ensure this new user has an organization. Then, add the new user credentials to `spec/fixtures/credentials.yml`
 - Mark 1 ticket as solved, change end-users email to on your can receive, copy ticket url, login as end-user (do not just assume identity), rate it
 - Create a new ticket and cc "zendesk-api-client-ruby-end-user-#{client.config.username}" (run tests once to create this user)
 - Suspend "zendesk-api-client-ruby-anonymous-#{client.config.username}" account, so tickets created by this account go to suspended
 - Ensure you allow admins to set up user password (or `POST /api/v2/users/{user_id}/password.json` will fail). You can check this in the admin centre > security > advanced
 - Go to Account > Localization and ensure you add `Spanish` to the list of additional languages. The `variant_spec` needs to create some items using spanish locale.
 - Ensure the authenticated agent is the assigned to the main fixture ticket at `spec/fixtures/zendesk.rb`, or the `activities_spec` won't get any update, and thus, will fail.