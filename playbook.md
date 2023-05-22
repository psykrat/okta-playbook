# Okta Security Incident Investigation Playbook

## 1. Incident Identification

Start by identifying and understanding the nature of the incident. This may include but is not limited to unauthorized access, suspicious activity, policy violations, etc. Gather all available data about the incident.

Common Okta logs to check:
```markdown
eventType eq "user.session.start" and outcome.result eq "FAILURE"
eventType eq "user.mfa.factor.verify" and outcome.result eq "FAILURE"
eventType eq "user.account.lock"
```

## 2. Document the Incident

Document all the details of the incident. This should include the date, time, user IDs involved, applications involved, IP addresses, and any other relevant information.

## 3. Investigation

Begin your investigation based on the nature of the incident.

- **Unauthorized Access**: Look at logs for any successful login attempts, especially from unfamiliar IP addresses or unusual locations. 

```markdown
eventType eq "user.session.start" and client.ipAddress eq "<suspicious_ip_address>"
```

- **Suspicious Activity**: Look at logs for policy changes, MFA changes, password changes, group changes, etc.

```markdown
eventType eq "user.mfa.factor.enroll"
eventType eq "user.mfa.factor.unenroll"
eventType eq "user.password.change"
eventType eq "group.user_membership.add"
eventType eq "group.user_membership.remove"
eventType eq "policy.lifecycle.create"
eventType eq "policy.lifecycle.update"
eventType eq "policy.lifecycle.delete"
```

## 4. Expand Your Scope

Once you've identified the user(s) involved, consider expanding your scope to other related areas. Look at other actions taken by the user, other users with similar roles, or other activities on the same applications.

## 5. Involve Relevant Parties

Keep all relevant parties informed during the investigation. This might include management, legal, HR, or other IT teams.

## 6. Formulate a Response

Once you have all the details, formulate a response. This might involve changing passwords, updating policies, modifying user roles, and other remediation activities.

## 7. Post-Incident Review

After the incident has been resolved, conduct a post-incident review. Identify any areas for improvement in your security policies, user training, or incident response procedures.

This playbook is designed to be a starting point and should be adapted to fit your organization's specific needs.

Remember to replace `<suspicious_ip_address>` with the actual suspicious IP address you're investigating.

### Useful Links:

- [Okta Expression Language Documentation](https://developer.okta.com/docs/reference/okta-expression-language/)
- [Okta System Log Documentation](https://developer.okta.com/docs/reference/api/system-log/)
- [Okta System Log Events](https://developer.okta.com/docs/reference/api/event-types/)
