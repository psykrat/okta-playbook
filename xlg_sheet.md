# okta-xlg-cheatsheet

**Note:** Replace `<user_id>`, `<group_id>`, `<application_id>` with actual user ID, group ID, or application ID respectively.

### User Application Access
```
eventType eq "user.session.start" and target.id eq "<user_id>"
```

### Application Assignments
```
eventType eq "app.user_membership.add" and target.id eq "<application_id>"
```

### Group Assignments
```
eventType eq "group.user_membership.add" and target.id eq "<group_id>"
```

### Application Removal
```
eventType eq "app.user_membership.remove" and target.id eq "<application_id>"
```

### Group Removal
```
eventType eq "group.user_membership.remove" and target.id eq "<group_id>"
```

### Successful User Authentication
```
eventType eq "user.authentication.sso" and outcome.result eq "SUCCESS"
```

### Failed User Authentication
```
eventType eq "user.authentication.sso" and outcome.result eq "FAILURE"
```

### User Locked Out
```
eventType eq "user.account.lock"
```

### User Unlocked
```
eventType eq "user.account.unlock"
```

### User Password Change
```
eventType eq "user.password.change"
```

### User Password Reset
```
eventType eq "user.password.reset"
```

### MFA (Multi-Factor Authentication) Enrollment
```
eventType eq "user.mfa.factor.enroll"
```

### MFA Unenrollment
```
eventType eq "user.mfa.factor.unenroll"
```

### MFA Challenge Success
```
eventType eq "user.mfa.factor.verify" and outcome.result eq "SUCCESS"
```

### MFA Challenge Failure
```
eventType eq "user.mfa.factor.verify" and outcome.result eq "FAILURE"
```

### New Device Used for Authentication
```
eventType eq "user.session.start" and client.device eq "New"
```

### User Account Deactivation
```
eventType eq "user.lifecycle.deactivate"
```

### User Account Activation
```
eventType eq "user.lifecycle.activate"
```

### API Token Created
```
eventType eq "application.token.create"
```

### API Token Revoked
```
eventType eq "application.token.revoke"
```

### User Added to Application
```markdown
eventType eq "app.user_membership.add" and target.id eq "<application_id>"
```

### User Removed from Application
```markdown
eventType eq "app.user_membership.remove" and target.id eq "<application_id>"
```

### User Added to Group
```markdown
eventType eq "group.user_membership.add" and target.id eq "<group_id>"
```

### User Removed from Group
```markdown
eventType eq "group.user_membership.remove" and target.id eq "<group_id>"
```

### Policy Assigned to Group
```markdown
eventType eq "policy.rule.activate" and target.id eq "<group_id>"
```

### Policy Removed from Group
```markdown
eventType eq "policy.rule.deactivate" and target.id eq "<group_id>"
```

### Policy Created
```markdown
eventType eq "policy.lifecycle.create"
```

### Policy Updated
```markdown
eventType eq "policy.lifecycle.update"
```

### Policy Deleted
```markdown
eventType eq "policy.lifecycle.delete"
```

### Policy Activated
```markdown
eventType eq "policy.lifecycle.activate"
```

### Policy Deactivated
```markdown
eventType eq "policy.lifecycle.deactivate"
```

### Policy Assigned to User
```markdown
eventType eq "policy.rule.user_whitelist.add" and target.id eq "<user_id>"
```

### Policy Unassigned from User
```markdown
eventType eq "policy.rule.user_whitelist.remove" and target.id eq "<user_id>"
```

### Sign-on Policy Updated
```markdown
eventType eq "policy.evaluate_sign_on"
```

## Tips for usage

- **`eq`** is the operator for **equals** in Okta expression language. 

- **`target.id`** refers to the object of the action (like user, group, app) and it's often used with `eq` operator. 

- **`eventType`** is used to specify the type of event you're searching for. 

- **`outcome.result`** refers to the result of the event and it's often used with `eq` operator.

- **`client.device`** refers to the device used for the event.

- Make sure to replace `<user_id>`, `<group_id>`, and `<application_id>` with actual IDs in your Okta organization. 

**Disclaimer:** It's important to know that actual query may differ depending on your organization's log structure and events. Always refer to your organization's documentation or Okta's official documentation for accurate information.

### Useful Links:

- [Okta Expression Language Documentation](https://developer.okta.com/docs/reference/okta-expression-language/)
- [Okta System Log Documentation](https://developer.okta.com/docs/reference/api/system-log/)
- [Okta System Log Events](https://developer.okta.com/docs/reference/api/event-types/)
