---
permalink: /aws/:title
---

Recently I read a [post](https://www.reddit.com/r/aws/comments/8rj9ep/my_aws_account_was_hacked/) on Reddit about some poor soul getting his AWS account hacked.
Situations like this show that you got to have at least some kind of understanding when it comes to security to not get burnt.
Claiming otherwise won't take you anywhere.
Because of that I've prepared a small list of tips to follow to for anyone who would like to improve his AWS account security.

## Few tips for account management

* Multi-Factor Authentication (MFA)
    * Root user account - As a root can do pretty much anything he wants, it's better to secure those with an external source of authentication
    A common practice is to at least require Virtual MFA but I would say it's not enough and a Physical U2F [Key](https://www.amazon.com/Yubico-YubiKey-USB-Two-Factor-Authentication/dp/B018Y1Q71M?ref=ast_p_ep) is a lot better
    * Non-root user accounts - For those at least require Virtual MFA - Microsoft or Google Authenticator are pretty nice for that
- Credentials rotation - often
    * AWS Access Key and Secret Key - All it takes is to generate them again and invalidate the old ones. I would say doing it on a monthly basis is enough
    * Console Password - Quarterly reset does the job
- IAM Password Policy
    * A good thing to have when your users love an _easy to remember_ passwords (looking at you "querty1234"..)
- Split responsibility - protects from and makes it easier to pinpoint a source of a breach
    * Users - don't grant them an access to everything there is. Each user should have an access only to required services
    * Automation - create a separate users/roles with only required services access (check out Assume-Role/Instance-Profile API)
- SSH Keys separation - also protects from and makes it easier to pinpoint a source of a breach
    * Don't use a master ssh key as a "general purpose key", instead generate ssh key for each team member
- S3 buckets
    * By default they are private - keep in mind that making them public exposes them to the web (responsible usage)
- KMS Keys
    * Rotate encryption keys from time to time - you can offload that duty to AWS
- CloudWatch/S3 Bucket - logs delete protection
    * It's an often practice for hackers to remove the logs of their activity, make it harder for them
- CloudWatch Billing Alarm
    * To learn how to do that follow [this](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) guideline

There are also some general tips to security that could apply here like:

- Don't store passwords in version control (API Keys / Tokens etc)
- Don't expose unnecessary ports on public servers
- Install security updates (Which often comes down to updating AWS Ami version)

Of course there is a lot more one could do, but this list significantly reduces the chances of you getting your AWS account compromised.
_In case_ you are interested in how to perform a "Security Audit" of your AWS account I would advice to go through the extensive [documentation](https://docs.aws.amazon.com/general/latest/gr/aws-security-audit-guide.html)
provided by Amazon.