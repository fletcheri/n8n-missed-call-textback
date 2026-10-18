# Missed-Call Text-Back (Lite): free n8n workflow for Australian businesses

When you miss a call, the caller gets an instant SMS from your business number, so they don't ring someone else.

- Twilio voice webhook in → TwiML voice message plus SMS to the caller
- AU number normalisation (04xx → +614xx); only texts mobiles, skips landlines
- 12-hour dedupe so repeat callers aren't spammed
- STOP/START opt-out handling (Spam Act 2003: every text has your business name and "Reply STOP to opt out")

## Setup (about 20 minutes)
1. n8n → **Import from file** → `workflow/missed-call-textback-lite.n8n.json`.
2. Open **Decide** and set `businessName`, `smsFrom` (your Twilio AU mobile number in +61 format) and `twilioAccountSid`.
3. On **Send SMS (Twilio)**, add an HTTP Basic Auth credential: User = Account SID, Password = Auth Token.
4. Activate. In Twilio, set your number's **Voice** webhook to `https://<your-n8n>/webhook/missed-call` and its **Messaging** webhook to `https://<your-n8n>/webhook/sms-inbound`.
5. Forward unanswered calls from your mobile to the Twilio number: dial `**61*<twilio number>#`, plus `**67*…#` for busy and `**62*…#` for unreachable. Cancel them all with `##004#`. Check your carrier's charges.

Costs (Twilio, Oct 2026): about US$0.0515 (≈A$0.074) per SMS and US$8.25/month (≈A$11.90) for an AU mobile number, plus voice minutes.

## Want more?
The **Pro pack** adds:
- a hosted-anywhere quote form with lead references
- owner alert texts for missed calls, replies and quotes
- customer replies forwarded to you
- business-hours and after-hours messages
- ClickSend support, plus dry-run mode
- AI job triage
- cost caps and webhook secrets
- an AU compliance guide, setup docs and test scripts

**Want the full Australian version?** The Tradie Missed-Call Pack (Pro) adds a quote form, owner alerts with reply forwarding, business-hours and after-hours messages, ClickSend support, dry-run mode, AI triage, SMS cost caps and full setup and compliance docs. Store link coming soon; questions to aussieflows@mail.grokbot.com.

[Notify me when Pro is out](mailto:aussieflows@mail.grokbot.com?subject=Notify%20me%20-%20Tradie%20Missed-Call%20Pack).

## More free AU workflows
Other free n8n workflows for Australian small businesses (MIT, same setup style):
- [Google Review Request](https://github.com/fletcheri/n8n-google-review-request): one honest Google review ask after each job
- [Quote Follow-Up](https://github.com/fletcheri/n8n-quote-follow-up): a polite follow-up SMS after you send a quote
- [Booking Reminder](https://github.com/fletcheri/n8n-booking-reminder): a reminder SMS before each booking
- [Overdue Invoice Reminder](https://github.com/fletcheri/n8n-overdue-invoice-reminder): an overdue-invoice email a week after the due date

MIT licence. Not legal advice.
