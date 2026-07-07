# Email Blocklist

A continuously maintained blocklist of **outreach-spam senders** — cold-email blasters, lead-gen scrapers, "quick question" merger/loan/SEO pitches — harvested from real blocked mail across several business mailboxes.

**The list:** [`blocklist.txt`](blocklist.txt) — one entry per line, ready to paste or import.

## Entry formats

| Entry | Meaning |
|---|---|
| `*@domain.com` | blocks every sender at `domain.com` |
| `user@gmail.com` | blocks one specific address (used for shared providers, so gmail/outlook/etc. are never blocked wholesale) |
| `*.domain.com` | blocks all subdomains of `domain.com` |

Shared consumer/business providers (Gmail, Yahoo, Outlook, iCloud, PayPal, DocuSign, …) are deliberately **never** domain-blocked — only individual abusive addresses from those providers appear here.

## How to use it

**Intermedia (HostPilot):** Services > Email Protection > Inbound Policies > *your policy* > Blocked Senders > **Import from TXT** — upload or paste `blocklist.txt` (comment lines starting with `#` are ignored by most importers; strip them if yours complains). There is no entry-count limit.

**cPanel / other hosts:** most "blocked senders" or spam-filter text boxes accept the same one-entry-per-line format. Strip the `#` header lines if needed:

```bash
grep -v '^#' blocklist.txt | grep -v '^$' > clean.txt
```

## Caveats

- This reflects **one operator's spam**. Review before importing — your legitimate contacts may differ.
- Domain wildcards are aggressive by design: if you do business with a listed domain, remove that line first.
- Updates land as new commits; watch or pull this repo to stay current. Git history is the changelog.

## Removal requests

If your domain is listed and you believe that's wrong, open an issue — include the domain and why it shouldn't be here.

## License

[CC0 1.0](LICENSE) — public domain. Use it however you like.
