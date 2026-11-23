# Instance Cloud estate preflight

A read-only check of your AWS organisation before Instance Cloud sets up its tooling there. It reads your
organisation's settings and tells you what needs doing first. It changes nothing in your AWS accounts.

## Run it

In AWS CloudShell, signed in to your organisation's management account as an administrator:

```
rm -f estate-preflight.py ~/preflight-report.json
curl -fsSLO https://github.com/Instance-Cloud-Technology/estate-preflight/releases/latest/download/estate-preflight.py
echo "<SHA-256 from Instance Cloud>  estate-preflight.py" | sha256sum -c - \
  && { python3 estate-preflight.py; python3 estate-preflight.py --json > ~/preflight-report.json; }
```

Nothing runs unless the file matches the SHA-256 Instance Cloud sent you. If it doesn't match, a newer release
may have been published since: ask Instance Cloud for the current SHA-256, or download the exact release they
named from the [releases](https://github.com/Instance-Cloud-Technology/estate-preflight/releases) page.

The first run shows the results on screen. The second saves the same results as `preflight-report.json` in
your CloudShell home folder. It holds your organisation and account IDs, the identity you ran it as, and the result of each check.
Download it and send it to Instance Cloud, whatever the result.

## Licence

Proprietary. You may download, inspect and run it to prepare for onboarding with Instance Cloud. See
[LICENSE](LICENSE).
