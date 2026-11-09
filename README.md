# SMTP bounce codes

A plain-English list of **166 email bounce codes** from Gmail, Microsoft 365, Yahoo and the SMTP standard.
For each one: what the server says, what it means, whether it is a hard or soft bounce, and whose move it is to fix it.

Codes in **links** have a full page with causes, fixes and FAQ on [BounceLens](https://bouncelens.com/bounce-codes/).
To decode a whole bounce message, paste it into the free [bounce code lookup](https://bouncelens.com/bounce-code-lookup/). It runs in your browser.

- [Full guides](#full-guides)
- [Gmail and Google Workspace](#gmail-and-google-workspace)
- [Microsoft 365, Outlook.com and Exchange Online](#microsoft-365-outlookcom-and-exchange-online)
- [Yahoo and AOL](#yahoo-and-aol)
- [Standard codes (any mail server)](#standard-codes-any-mail-server)
- [How to read a bounce code](#how-to-read-a-bounce-code)
- [Machine-readable data](#machine-readable-data)

## Full guides

| Code | Error text | Seen at |
|---|---|---|
| [550 5.4.1](https://bouncelens.com/bounce-codes/550-5-4-1-recipient-address-rejected-access-denied/) | Recipient address rejected: Access denied | Microsoft 365 |
| [550 5.1.10](https://bouncelens.com/bounce-codes/550-5-1-10-recipient-not-found/) | Recipient not found | Microsoft 365 |
| [550 5.1.8](https://bouncelens.com/bounce-codes/550-5-1-8-access-denied-bad-outbound-sender/) | Access denied, bad outbound sender | Microsoft 365 |
| [550 5.1.90](https://bouncelens.com/bounce-codes/550-5-1-90-daily-limit-for-message-recipients/) | Daily limit for message recipients reached | Microsoft 365 |
| [550 5.2.2](https://bouncelens.com/bounce-codes/550-5-2-2-submission-quota-exceeded/) | Submission quota exceeded | Microsoft 365 |
| [550 5.2.121](https://bouncelens.com/bounce-codes/550-5-2-121-recipient-per-hour-limit-from-sender/) | Recipient's per hour message receive limit from specific sender exceeded | Microsoft 365 |
| [550 5.2.122](https://bouncelens.com/bounce-codes/550-5-2-122-recipient-per-hour-receive-limit/) | Recipient's per hour message receive limit exceeded | Microsoft 365 |
| [550 5.7.23](https://bouncelens.com/bounce-codes/550-5-7-23-spf-violation/) | Rejected because of Sender Policy Framework violation | Microsoft 365 |
| [530 5.7.57](https://bouncelens.com/bounce-codes/530-5-7-57-client-not-authenticated/) | Client was not authenticated to send anonymous mail during MAIL FROM | Microsoft 365 |
| [550 5.7.124](https://bouncelens.com/bounce-codes/550-5-7-124-sender-not-in-allowed-senders-list/) | Sender not in allowed-senders list | Microsoft 365 |
| [550 5.7.133](https://bouncelens.com/bounce-codes/550-5-7-133-sender-not-authenticated-for-group/) | Sender not authenticated for group | Microsoft 365 |
| [550 5.7.509](https://bouncelens.com/bounce-codes/550-5-7-509-dmarc-verification-failed-policy-reject/) | Sending domain does not pass DMARC verification | Microsoft 365 |
| [550 5.7.511](https://bouncelens.com/bounce-codes/550-5-7-511-access-denied-banned-sender/) | Access denied, banned sender | Microsoft 365 |
| [550 5.7.520](https://bouncelens.com/bounce-codes/550-5-7-520-external-forwarding-not-allowed/) | Your organization does not allow external forwarding | Microsoft 365 |
| [550 5.7.606](https://bouncelens.com/bounce-codes/550-5-7-606-access-denied-banned-sending-ip/) | Access denied, banned sending IP | Microsoft 365 |
| [553 5.1.2](https://bouncelens.com/bounce-codes/553-5-1-2-address-not-found-domain-could-not-be-found/) | Address not found, domain couldn't be found | Gmail |
| [550 5.1.1](https://bouncelens.com/bounce-codes/550-5-1-1-email-account-does-not-exist/) | The email account that you tried to reach does not exist | Gmail |
| [550 5.2.1](https://bouncelens.com/bounce-codes/550-5-2-1-email-account-inactive/) | The email account that you tried to reach is inactive | Gmail |
| [452 4.2.2](https://bouncelens.com/bounce-codes/452-4-2-2-recipient-inbox-out-of-storage/) | The recipient's inbox is out of storage space | Gmail |
| [421 4.7.0](https://bouncelens.com/bounce-codes/421-4-7-0-low-reputation-rate-limited/) | Temporarily rate limited: low reputation of the sending IP | Gmail |
| [421 4.7.28](https://bouncelens.com/bounce-codes/421-4-7-28-unusual-rate-of-email/) | Gmail has detected an unusual rate of email | Gmail |
| [550 5.7.1](https://bouncelens.com/bounce-codes/550-5-7-1-likely-unsolicited-mail/) | This message is likely unsolicited mail | Gmail |
| [550 5.7.26](https://bouncelens.com/bounce-codes/550-5-7-26-unauthenticated-sender/) | This email has been blocked because the sender is unauthenticated | Gmail |
| [550 5.7.25](https://bouncelens.com/bounce-codes/550-5-7-25-no-ptr-record/) | The sending IP address doesn't have a PTR record | Gmail |
| [550 5.4.5](https://bouncelens.com/bounce-codes/550-5-4-5-daily-user-sending-limit-exceeded/) | Daily user sending limit exceeded | Gmail |
| [552 5.3.4](https://bouncelens.com/bounce-codes/552-5-3-4-message-size-limit-exceeded/) | Your message exceeded Google's message size limits | Gmail |

## How to read a bounce code

A bounce usually has two codes, for example `550 5.1.1`:

| Part | Example | Meaning |
|---|---|---|
| Basic code | `550` | `4xx` = temporary (soft bounce, the sender retries). `5xx` = permanent (hard bounce). |
| Enhanced code, class | `5`.1.1 | Same idea: `4` temporary, `5` permanent, `2` success. |
| Enhanced code, subject | 5.`1`.1 | `1` address, `2` mailbox, `3` mail system, `4` network/routing, `5` protocol, `6` content, `7` security/policy. |
| Enhanced code, detail | 5.1.`1` | The exact problem. `5.1.1` = no such user. |

The same code can mean different things at different providers. Gmail `550 5.7.1` and Microsoft `550 5.7.1` have different causes, so always read the text after the code too.

**Whose move** tells you who can fix it:

| Value | Meaning |
|---|---|
| Fix your list | The address is bad. Fix the typo or remove it from your list. |
| Fix your sending setup | Your sending setup (SPF, DKIM, DMARC, IP, account limits) needs a fix. |
| Change the message | Something in the message itself (size, content, format) was refused. |
| Only the recipient side can fix it | Only the recipient's mail admin can change this. |
| Wait and try again | Temporary. Send less, then try again later. |

## Gmail and Google Workspace

Wording from [Gmail / Google Workspace](https://support.google.com/a/answer/3726730). 57 codes.

| Code | Server says | What it means | Type | Whose move |
|---|---|---|---|---|
| `450 4.2.1` | The user you are trying to contact is receiving email at a rate that prevents additional messages from being delivered. | This Gmail user is getting mail faster than Gmail allows. | soft | Wait and try again |
| `450 4.2.1` | Peak SMTP relay limit exceeded for this customer. | Your Google Workspace account sent too much through the SMTP relay. | soft | Wait and try again |
| [`452 4.2.2`](https://bouncelens.com/bounce-codes/452-4-2-2-recipient-inbox-out-of-storage/) | The recipient's inbox is out of storage space. | The recipient's Google storage is full. | soft | Wait and try again |
| `451 4.3.0` | Email server has temporarily rejected this message. | Gmail had a temporary problem. | soft | Wait and try again |
| `451 4.4.2` | Timeout - closing connection. | The connection to Gmail timed out. | soft | Wait and try again |
| `421 4.4.5` | Server busy, try again later. | Gmail was busy. | soft | Wait and try again |
| `451 4.5.0` | SMTP protocol violation. | The sending server broke the SMTP rules. | soft | Fix your sending setup |
| `452 4.5.3` | Your message has too many recipients. | Too many recipients in one message for Gmail. | soft | Change the message |
| `421 4.7.0` | The IP address sending this message does not have a PTR record, or the corresponding forward DNS entry does not point to the sending IP. | Gmail slowed you down because the sending IP has no reverse DNS. | soft | Fix your sending setup |
| [`421 4.7.0`](https://bouncelens.com/bounce-codes/421-4-7-0-low-reputation-rate-limited/) | This message is suspicious due to the very low reputation of the sending IP address. […] email sent from your IP address has been temporarily rate limited. | Gmail does not trust the sending IP or domain yet and is slowing your mail down. | soft | Fix your sending setup |
| `421 4.7.0` | TLS required for RCPT domain, closing connection. | The recipient's domain only accepts mail over TLS or from listed IPs. | soft | Fix your sending setup |
| `454 4.7.0` | Too many login attempts, please try again later. | The sending app could not log in to Gmail. | soft | Fix your sending setup |
| `421 4.7.0` | Try again later, closing connection. | Gmail closed the connection for now. | soft | Wait and try again |
| `451 4.7.23` | The sending IP address for this message doesn't have a PTR record, or the PTR record's forward DNS entry doesn't match the sending IP address. | Gmail slowed you down because the sending IP has no reverse DNS. | soft | Fix your sending setup |
| `451 4.7.24` | The SPF record of the sending domain has one or more suspicious entries. | Your SPF record looks unsafe to Gmail. | soft | Fix your sending setup |
| `421 4.7.26` | This email has been rate limited because it is unauthenticated. Gmail requires all senders to authenticate with either SPF or DKIM. | Neither SPF nor DKIM passed, so Gmail is slowing your mail down. | soft | Fix your sending setup |
| `421 4.7.27` | Your email has been rate limited because SPF authentication didn't pass for this message. | SPF did not pass. | soft | Fix your sending setup |
| [`421 4.7.28`](https://bouncelens.com/bounce-codes/421-4-7-28-unusual-rate-of-email/) | Gmail has detected an unusual rate of email. To protect our users from spam, email has been temporarily rate limited. | You sent too much, too fast, for Gmail. | soft | Fix your sending setup |
| `421 4.7.29` | Your email has been rate limited because you're not using a TLS connection. | The sending server does not use TLS. Gmail requires it for bulk senders. | soft | Fix your sending setup |
| `421 4.7.30` | Your email has been rate limited because DKIM authentication didn't pass for this message. | DKIM did not pass. | soft | Fix your sending setup |
| `421 4.7.32` | Your email has been rate limited because the From: header (RFC5322) in this message isn't aligned with either the authenticated SPF or DKIM organizational domain. | The From address does not match the domain that passed SPF or DKIM (DMARC alignment). | soft | Fix your sending setup |
| `421 4.7.40` | Your email has been rate limited because the sending domain doesn't have a DMARC record, or the DMARC record doesn't specify a DMARC policy. | Your domain has no DMARC record. | soft | Fix your sending setup |
| [`550 5.1.1`](https://bouncelens.com/bounce-codes/550-5-1-1-email-account-does-not-exist/) | The email account that you tried to reach does not exist. | There is no Gmail or Google Workspace mailbox with this address. | hard | Fix your list |
| [`553 5.1.2`](https://bouncelens.com/bounce-codes/553-5-1-2-address-not-found-domain-could-not-be-found/) | We weren't able to find the recipient domain. | The domain after the @ was not found. | hard | Fix your list |
| `553 5.1.3` | The recipient address is not a valid RFC 5321 address. | The address is not written in a valid way. | hard | Fix your list |
| `553 5.1.7` | The sender address is not a valid RFC 5321 address. | Your own sender address is not written in a valid way. | hard | Change the message |
| `550 5.2.1` | The user you are trying to contact is receiving email at a rate that prevents additional messages from being delivered. | This Gmail user is getting mail faster than Gmail allows. | hard | Wait and try again |
| [`550 5.2.1`](https://bouncelens.com/bounce-codes/550-5-2-1-email-account-inactive/) | The email account that you tried to reach is inactive. | The Google account is disabled or inactive. | hard | Fix your list |
| `552 5.2.2` | The recipient's inbox is out of storage space and inactive. | The recipient's storage is full and the account is not being used. | hard | Wait and try again |
| [`552 5.3.4`](https://bouncelens.com/bounce-codes/552-5-3-4-message-size-limit-exceeded/) | Your message exceeded Google's message size limits. | The message, an attachment or a header is over Gmail’s size limit. | hard | Change the message |
| [`550 5.4.5`](https://bouncelens.com/bounce-codes/550-5-4-5-daily-user-sending-limit-exceeded/) | Daily user sending limit exceeded. | Your Gmail account reached its daily sending limit. | hard | Wait and try again |
| `554 5.4.6` | Message exceeded 50 hops, this may indicate an email loop. | The message was passed between servers more than 50 times. | hard | Only the recipient side can fix it |
| `503 5.5.1` | Bad sequence of commands. | The sending server sent SMTP commands in the wrong order. | hard | Fix your sending setup |
| `555 5.5.2` | Syntax error. | The sending server sent a command Gmail could not read. | hard | Fix your sending setup |
| `550 5.5.3` | Too many recipients for this sender. | Too many recipients in one message for Gmail. | hard | Change the message |
| `501 5.5.4` | HELO/EHLO argument invalid, closing connection. | The sending server introduced itself with an invalid name. | hard | Fix your sending setup |
| `554 5.6.0` | Email message is malformed. Not accepted. | The email is not built according to the standard. | hard | Change the message |
| `552 5.7.0` | This message was blocked because its content presents a potential security issue. | Gmail blocks this kind of attachment or content. | hard | Change the message |
| `550 5.7.0` | Email relay denied. […] Email is being sent from a domain or IP address which isn't registered in your Workspace account. | The Google Workspace SMTP relay does not accept mail from this server or domain. | hard | Fix your sending setup |
| `530 5.7.0` | Authentication required. | The sending app must log in (and use STARTTLS) before sending. | hard | Fix your sending setup |
| [`550 5.7.1`](https://bouncelens.com/bounce-codes/550-5-7-1-likely-unsolicited-mail/) | This message is likely unsolicited email. To reduce the amount of spam sent to Gmail, this message has been blocked. | Gmail treated the message as spam and refused it. | hard | Fix your sending setup |
| `550 5.7.1` | Messages missing a valid Message-ID: header are not accepted. | The email headers break the rules Gmail checks. | hard | Change the message |
| `550 5.7.1` | This message does not meet IPv6 sending guidelines regarding PTR records and authentication. | Mail sent over IPv6 needs reverse DNS and authentication. | hard | Fix your sending setup |
| `550 5.7.1` | The IP you're using to send email is not authorized to send email directly to our servers. | This IP address may not send straight to Gmail. Send through your provider’s mail server. | hard | Fix your sending setup |
| `550 5.7.1` | The user or domain that you are sending to (or from) has a policy that prohibits the email that you sent. | A rule set by the recipient’s (or your own) administrator blocked the message. | hard | Only the recipient side can fix it |
| `534 5.7.14` | Please log in through your web browser and then try again. | Google stopped the sign-in from the sending app. | hard | Fix your sending setup |
| `550 5.7.24` | The SPF record of the sending domain has one or more suspicious entries. | Your SPF record looks unsafe to Gmail. | hard | Fix your sending setup |
| [`550 5.7.25`](https://bouncelens.com/bounce-codes/550-5-7-25-no-ptr-record/) | This message was blocked because the sending IP address doesn't have a PTR record, or the forwarding DNS entry doesn't reference the sending IP address. | The sending IP has no reverse DNS. | hard | Fix your sending setup |
| [`550 5.7.26`](https://bouncelens.com/bounce-codes/550-5-7-26-unauthenticated-sender/) | This email has been blocked because the sender is unauthenticated. Gmail requires all senders to authenticate with either SPF or DKIM. | Neither SPF nor DKIM passed, or the message failed your domain’s DMARC policy. | hard | Fix your sending setup |
| `550 5.7.27` | This message was blocked because it didn't pass SPF authentication. | SPF did not pass. | hard | Fix your sending setup |
| `550 5.7.28` | There is an unusual rate of unsolicited email originating from your IP address. | Gmail blocked the sending IP for sending too much unwanted mail. | hard | Fix your sending setup |
| `550 5.7.29` | This message was blocked because it wasn't sent over a TLS connection. | The sending server does not use TLS. Gmail requires it for bulk senders. | hard | Fix your sending setup |
| `550 5.7.30` | This message was blocked because it didn't pass DKIM authentication. | DKIM did not pass. | hard | Fix your sending setup |
| `550 5.7.32` | Your email was blocked because the From: header (RFC5322) in this message isn't aligned with either the authenticated SPF or DKIM organizational domain. | The From address does not match the domain that passed SPF or DKIM (DMARC alignment). | hard | Fix your sending setup |
| `550 5.7.40` | Your message was blocked because the sending domain doesn't have a DMARC record or the DMARC record doesn't specify a DMARC policy. | Your domain has no DMARC record. | hard | Fix your sending setup |
| `535 5.7.80` | Username and Password not accepted. | The sending app has the wrong Gmail username or password. | hard | Fix your sending setup |
| `534 5.7.90` | Application-specific password required. | The sending app needs a Google app password. | hard | Fix your sending setup |

## Microsoft 365, Outlook.com and Exchange Online

Wording from [Microsoft 365 / Outlook](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online). 66 codes.

| Code | Server says | What it means | Type | Whose move |
|---|---|---|---|---|
| `432 4.3.2` | STOREDRV.Deliver; recipient thread limit exceeded | The recipient’s mailbox is getting too many messages too quickly. | soft | Wait and try again |
| `4.4.7` | Message expired | Microsoft kept trying to deliver the message and gave up. | soft | Wait and try again |
| `X.4.8` | MX hosts of &lt;domain&gt; failed MTA-STS validation | The recipient’s mail server does not match their own MTA-STS security policy. | soft or hard | Only the recipient side can fix it |
| `4.4.316` | Connection refused [Message=Socket error code 10061] | The recipient’s mail server refused every connection. | soft | Wait and try again |
| `4.5.3` | Too many recipients | More than 200 recipients at the same domain in one message. | soft | Change the message |
| `X.7.5` | Remote certificate failed MTA-STS validation. | The recipient’s mail server certificate is not trusted. | soft or hard | Only the recipient side can fix it |
| `4.7.26` | Access denied, a message sent over IPv6 must pass either SPF or DKIM validation, this message is not signed | Mail sent over IPv6 must pass SPF or DKIM. | soft | Fix your sending setup |
| `X.7.321` | starttls-not-supported: Destination mail server must support TLS to receive mail. | The recipient’s mail server does not support TLS. | soft or hard | Only the recipient side can fix it |
| `X.7.322` | certificate-expired: Destination mail server's certificate is expired. | The recipient’s mail server certificate has expired. | soft or hard | Only the recipient side can fix it |
| `X.7.323` | tlsa-invalid: The domain failed DANE validation. | The recipient’s domain failed a DANE security check. | soft or hard | Only the recipient side can fix it |
| `X.7.324` | dnssec-invalid: Destination domain returned invalid DNSSEC records | The recipient’s domain has broken DNSSEC records. | soft or hard | Only the recipient side can fix it |
| `X.7.325` | certificate-host-mismatch: Remote certificate MUST have a common name or subject alternative name matching the hostname (DANE) | The recipient’s mail server certificate is for a different host name. | soft or hard | Only the recipient side can fix it |
| `4.7.500-699` | Access denied, please try again later | Microsoft saw suspicious activity and paused your sending for a while. | soft | Fix your sending setup |
| `4.7.850-899` | Access denied, please try again later | Microsoft saw suspicious activity from the sending IP and paused it for a while. | soft | Fix your sending setup |
| `550 5.0.350` | Generic error, x-dg-ref header is too long, or Requested action not taken: policy violation detected (AS345) | A catch-all code: the recipient’s mail system refused the message without a specific reason. | hard | Only the recipient side can fix it |
| `550 5.1.1` | Bad destination mailbox address | This mailbox does not exist at the recipient’s Microsoft 365 organisation. | hard | Fix your list |
| [`550 5.1.8`](https://bouncelens.com/bounce-codes/550-5-1-8-access-denied-bad-outbound-sender/) | Access denied, bad outbound sender | Microsoft blocked your account for sending too much spam, usually because it was hacked. | hard | Fix your sending setup |
| [`550 5.1.10`](https://bouncelens.com/bounce-codes/550-5-1-10-recipient-not-found/) | Recipient not found | This address was not found at the recipient’s Microsoft 365 organisation. | hard | Fix your list |
| [`550 5.1.90`](https://bouncelens.com/bounce-codes/550-5-1-90-daily-limit-for-message-recipients/) | Your message can't be sent because you've reached your daily limit for message recipients | You reached Microsoft’s daily limit for the number of recipients. | hard | Wait and try again |
| [`550 5.2.2`](https://bouncelens.com/bounce-codes/550-5-2-2-submission-quota-exceeded/) | Submission quota exceeded | You sent more recipients or messages than Microsoft allows. In Microsoft 365 this is about the sender, not a full mailbox. | hard | Wait and try again |
| [`550 5.2.121`](https://bouncelens.com/bounce-codes/550-5-2-121-recipient-per-hour-limit-from-sender/) | Recipient's per hour message receive limit from specific sender exceeded | You sent this recipient more messages in an hour than Microsoft allows from one sender. | hard | Wait and try again |
| [`550 5.2.122`](https://bouncelens.com/bounce-codes/550-5-2-122-recipient-per-hour-receive-limit/) | Recipient's per hour message receive limit exceeded | The recipient got more messages this hour than Microsoft allows. | hard | Wait and try again |
| [`550 5.4.1`](https://bouncelens.com/bounce-codes/550-5-4-1-recipient-address-rejected-access-denied/) | Recipient address rejected: Access denied | The address does not exist. Microsoft rejects unknown addresses at the door with this message. | hard | Fix your list |
| `550 5.4.1` | Relay Access Denied | The mail server that answered does not accept mail for this domain. | hard | Fix your list |
| `5.4.6` | Routing loop detected | A setup error on the recipient side sends the message in a circle. | hard | Only the recipient side can fix it |
| `5.4.14` | Routing loop detected | A setup error on the recipient side sends the message in a circle. | hard | Only the recipient side can fix it |
| `5.4.300` | Message expired | The recipient’s mail server did not accept the message in time. | hard | Wait and try again |
| `550 5.5.0` | Requested action not taken: mailbox unavailable | There is no Outlook.com or Hotmail mailbox with this address. | hard | Fix your list |
| `5.6.11` | Invalid characters | Your email program added characters (bare line feeds) the other server does not accept. | hard | Change the message |
| `550 5.7.1` | Unable to relay | The sending app or server is not logged in, or is not allowed to relay mail. | hard | Fix your sending setup |
| `550 5.7.1` | Delivery not authorized | You are not allowed to send to this recipient. | hard | Only the recipient side can fix it |
| `550 5.7.12` | Sender was not authenticated by organization | This address only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| [`550 5.7.23`](https://bouncelens.com/bounce-codes/550-5-7-23-spf-violation/) | The message was rejected because of Sender Policy Framework violation | SPF failed for the domain you send from. | hard | Fix your sending setup |
| `550 5.7.25` | Access denied, the sending IPv6 address must have a reverse DNS record | The sending IPv6 address has no reverse DNS. | hard | Fix your sending setup |
| [`530 5.7.57`](https://bouncelens.com/bounce-codes/530-5-7-57-client-not-authenticated/) | Client was not authenticated to send anonymous mail during MAIL FROM | The app or device sending through smtp.office365.com is not logged in correctly. | hard | Fix your sending setup |
| `550 5.7.64` | TenantAttribution; Relay Access Denied | The connector between your own mail server and Microsoft 365 is set up wrongly. | hard | Fix your sending setup |
| [`550 5.7.124`](https://bouncelens.com/bounce-codes/550-5-7-124-sender-not-in-allowed-senders-list/) | Sender not in allowed-senders list | You are not on the list of people allowed to write to this group. | hard | Only the recipient side can fix it |
| [`550 5.7.133`](https://bouncelens.com/bounce-codes/550-5-7-133-sender-not-authenticated-for-group/) | Sender not authenticated for group | This group address only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| `550 5.7.134` | Sender was not authenticated for mailbox | This mailbox only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| `550 5.7.13` | Sender was not authenticated for public folder | This public folder only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| `550 5.7.135` | Sender was not authenticated for public folder | This public folder only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| `550 5.7.136` | Sender was not authenticated | This address only accepts mail from inside its own organisation. | hard | Only the recipient side can fix it |
| `550 5.7.232` | Your message can't be sent because your trial tenant has exceeded its daily limit for sending email to external recipients | Your Microsoft 365 trial reached its daily limit for outside recipients. | hard | Wait and try again |
| `550 5.7.233` | Your message can't be sent because your tenant exceeded its daily limit for sending email to external recipients | Your Microsoft 365 organisation reached its daily limit for outside recipients. | hard | Wait and try again |
| `550 5.7.236` | Your message can't be sent because your tenant has exceeded its daily limit for sending email to external recipients from your tenant's onmicrosoft.com domains | You sent to more than 100 outside recipients in 24 hours from an onmicrosoft.com address. | hard | Wait and try again |
| `550 5.7.367` | Remote server returned not permitted to relay | SPF or DKIM failed on a forwarded or relayed message. | hard | Fix your sending setup |
| `550 5.7.501` | Access denied, spam abuse detected | Microsoft banned the sending account for spam. | hard | Fix your sending setup |
| [`550 5.7.502`](https://bouncelens.com/bounce-codes/550-5-7-511-access-denied-banned-sender/) | Access denied, banned sender | Microsoft banned the sending account for spam. | hard | Fix your sending setup |
| [`550 5.7.503`](https://bouncelens.com/bounce-codes/550-5-7-511-access-denied-banned-sender/) | Access denied, banned sender | Microsoft banned the sending account for spam. | hard | Fix your sending setup |
| [`550 5.7.504`](https://bouncelens.com/bounce-codes/550-5-4-1-recipient-address-rejected-access-denied/) | Recipient address rejected: Access denied | The recipient address is not valid. | hard | Fix your list |
| `550 5.7.505` | Access denied, banned recipient | The recipient address is not valid. | hard | Fix your list |
| `550 5.7.506` | Access Denied, Bad HELO | Your mail server introduces itself with the wrong name. | hard | Fix your sending setup |
| `550 5.7.507` | Access denied, rejected by recipient | The recipient’s organisation blocked the IP address you send from. | hard | Fix your sending setup |
| `550 5.7.508` | Access denied, [IP] has exceeded permitted limits within range | Your IPv6 range sent too many messages in a short time. | hard | Fix your sending setup |
| [`550 5.7.509`](https://bouncelens.com/bounce-codes/550-5-7-509-dmarc-verification-failed-policy-reject/) | Access denied, sending domain does not pass DMARC verification and has a DMARC policy of reject. | The message failed DMARC, and your domain’s own DMARC policy says to reject such mail. | hard | Fix your sending setup |
| `550 5.7.510` | Access denied, [domain] does not accept email over IPv6 | The recipient does not accept email over IPv6. | hard | Fix your sending setup |
| [`550 5.7.511`](https://bouncelens.com/bounce-codes/550-5-7-511-access-denied-banned-sender/) | Access denied, banned sender | Microsoft banned the IP address you send from. | hard | Fix your sending setup |
| `550 5.7.512` | Access denied, message must be RFC 5322 section 3.6.2 compliant | The message has no valid From address. | hard | Change the message |
| `550 5.7.513` | Service unavailable, Client host blocked by recipient domain using Customer Block list | The recipient’s domain put your sending IP on its own block list. | hard | Fix your sending setup |
| [`550 5.7.520`](https://bouncelens.com/bounce-codes/550-5-7-520-external-forwarding-not-allowed/) | Access denied, Your organization does not allow external forwarding. | Your own organisation blocks automatic forwarding to outside addresses. | hard | Only the recipient side can fix it |
| [`550 5.7.606-649`](https://bouncelens.com/bounce-codes/550-5-7-606-access-denied-banned-sending-ip/) | Access denied, banned sending IP | Microsoft banned the IP address you send from. | hard | Fix your sending setup |
| `550 5.7.703` | Your message can't be delivered because messages to XXX, YYY are blocked by your organization using Tenant Allow Block List. | Your own organisation blocks mail to this address or domain. | hard | Only the recipient side can fix it |
| `550 5.7.705` | Access denied, tenant has exceeded threshold | Microsoft stopped your whole organisation from sending because most of its mail looked suspicious. | hard | Fix your sending setup |
| `550 5.7.708` | Access denied, traffic not accepted from this IP | Microsoft does not accept mail from this IP address. | hard | Fix your sending setup |
| `550 5.7.750` | Service unavailable. Client blocked from sending from unregistered domains | Your organisation sent too much mail from domains not added to Microsoft 365. | hard | Fix your sending setup |
| [`550 5.7.800`](https://bouncelens.com/bounce-codes/550-5-7-511-access-denied-banned-sender/) | Access denied, banned sender | Microsoft banned your sending domain for spam. | hard | Fix your sending setup |

## Yahoo and AOL

Wording from [Yahoo / AOL](https://senders.yahooinc.com/smtp-error-codes/). 1 code.

| Code | Server says | What it means | Type | Whose move |
|---|---|---|---|---|
| `554` | 554 delivery error: dd This user doesn't have a yahoo.com account | There is no Yahoo mailbox with this address. | hard | Fix your list |

## Standard codes (any mail server)

Wording from [the SMTP standard](https://www.iana.org/assignments/smtp-enhanced-status-codes/smtp-enhanced-status-codes.xhtml). 42 codes. `X` stands for `4` (temporary) or `5` (permanent).

| Code | Server says | What it means | Type | Whose move |
|---|---|---|---|---|
| `X.1.0` | Other address status | Something is wrong with an address, but the code does not say what. | soft or hard | Fix your list |
| `550 X.1.1` | Bad destination mailbox address | The mailbox does not exist. | hard | Fix your list |
| `X.1.2` | Bad destination system address | The domain after the @ does not exist or cannot receive email. | soft or hard | Fix your list |
| `501 X.1.3` | Bad destination mailbox address syntax | The address is not written in a valid way. | hard | Fix your list |
| `X.1.6` | Destination mailbox has moved, No forwarding address | The mailbox has moved and left no new address. | soft or hard | Fix your list |
| `X.1.7` | Bad sender's mailbox address syntax | Your own sender address is not written in a valid way. | soft or hard | Change the message |
| `X.1.8` | Bad sender's system address | The domain of your own sender address is not valid. | soft or hard | Change the message |
| `556 X.1.10` | Recipient address has null MX | The domain says, on purpose, that it never receives email. | hard | Fix your list |
| `X.2.0` | Other or undefined mailbox status | Something is wrong with the mailbox, but the code does not say what. | soft or hard | Only the recipient side can fix it |
| `X.2.1` | Mailbox disabled, not accepting messages | The mailbox exists but is switched off. | soft or hard | Fix your list |
| `552 X.2.2` | Mailbox full | The mailbox is full. | hard | Wait and try again |
| `552 X.2.3` | Message length exceeds administrative limit | The message is bigger than this mailbox accepts. | hard | Change the message |
| `X.3.0` | Other or undefined mail system status | The mail system had a problem it did not name. | soft or hard | Wait and try again |
| `452 X.3.1` | Mail system full | The mail server (not the mailbox) is out of space. | soft | Wait and try again |
| `X.3.2` | System not accepting network messages | The mail server is not taking mail at the moment. | soft or hard | Wait and try again |
| `552 X.3.4` | Message too big for system | The message is bigger than the mail server accepts. | hard | Change the message |
| `X.4.0` | Other or undefined network or routing status | A network problem stopped delivery. | soft or hard | Wait and try again |
| `451 X.4.1` | No answer from host | The recipient’s mail server did not answer. | soft | Wait and try again |
| `421 X.4.2` | Bad connection | The connection to the recipient’s mail server broke. | soft | Wait and try again |
| `X.4.3` | Directory server failure | The mail server could not look the address up just now. | soft or hard | Wait and try again |
| `X.4.4` | Unable to route | No mail server could be found for the domain. | soft or hard | Fix your list |
| `451 X.4.5` | Mail system congestion | The mail server is overloaded. | soft | Wait and try again |
| `X.4.6` | Routing loop detected | The message is being passed round in a circle. | soft or hard | Only the recipient side can fix it |
| `X.4.7` | Delivery time expired | The message could not be delivered within the retry time. | soft or hard | Wait and try again |
| `X.5.0` | Other or undefined protocol status | The mail servers could not understand each other. | soft or hard | Fix your sending setup |
| `X.5.1` | Invalid command | The sending server sent a command the other side did not accept. | soft or hard | Fix your sending setup |
| `X.5.2` | Syntax error | The sending server sent a command the other side could not read. | soft or hard | Fix your sending setup |
| `451 X.5.3` | Too many recipients | Too many recipients in one message. | soft | Change the message |
| `X.5.4` | Invalid command arguments | The sending server sent a command with bad values. | soft or hard | Fix your sending setup |
| `X.6.0` | Other or undefined media error | The message content could not be handled. | soft or hard | Change the message |
| `X.7.0` | Other or undefined security status | Refused for a security or policy reason the code does not name. | soft or hard | Only the recipient side can fix it |
| `550 X.7.1` | Delivery not authorized, message refused | The recipient side refused the message by policy. This often means a spam filter or a block list. | hard | Only the recipient side can fix it |
| `535 X.7.8` | Authentication credentials invalid | The sending app has the wrong username or password. | hard | Fix your sending setup |
| `550 X.7.20` | No passing DKIM signature found | No DKIM signature on the message passed. | hard | Fix your sending setup |
| `550 X.7.21` | No acceptable DKIM signature found | No DKIM signature on the message was acceptable. | hard | Fix your sending setup |
| `550 X.7.22` | No valid author-matched DKIM signature found | No DKIM signature matched the From domain. | hard | Fix your sending setup |
| `550 X.7.23` | SPF validation failed | SPF failed for the domain you send from. | hard | Fix your sending setup |
| `550 X.7.24` | SPF validation error | The SPF record of your domain could not be checked. | hard | Fix your sending setup |
| `550 X.7.25` | Reverse DNS validation failed | The sending IP has no matching reverse DNS. | hard | Fix your sending setup |
| `550 X.7.26` | Multiple authentication checks failed | More than one of SPF, DKIM and DMARC failed. | hard | Fix your sending setup |
| `550 X.7.27` | Sender address has null MX | The domain of your sender address says it never receives email. | hard | Change the message |
| `X.7.28` | Mail flood detected | Too many messages arrived too fast. | soft or hard | Fix your sending setup |

## Machine-readable data

[`codes.json`](codes.json) has the same 166 rows:

```json
{
  "provider": "gmail",
  "smtp": "452",
  "enhanced": "4.2.2",
  "text": "The recipient's inbox is out of storage space.",
  "meaning": "The recipient's Google storage is full.",
  "type": "soft",
  "category": "Mailbox is full",
  "whose_move": "Wait and try again",
  "page": "https://bouncelens.com/bounce-codes/452-4-2-2-recipient-inbox-out-of-storage/"
}
```

## Sources

Provider wording is taken from each provider's own documentation:
- [Gmail / Google Workspace](https://support.google.com/a/answer/3726730)
- [Microsoft 365 / Outlook](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online)
- [Yahoo / AOL](https://senders.yahooinc.com/smtp-error-codes/)
- [the SMTP standard](https://www.iana.org/assignments/smtp-enhanced-status-codes/smtp-enhanced-status-codes.xhtml)

Last built 2026-11-09.

## Contributing

Seen a bounce that is not here, or wording that changed? [Open an issue](../../issues/new) with the full bounce text.
Remove email addresses and anything private first.

## License

Text and data: [CC BY 4.0](LICENSE). Made by [BounceLens](https://bouncelens.com), a free email list checker that runs in your browser.
