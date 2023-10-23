# Mailpit - email testing for developers

![Tests](https://github.com/axllent/mailpit/actions/workflows/tests.yml/badge.svg)
![Build status](https://github.com/axllent/mailpit/actions/workflows/release-build.yml/badge.svg)
![Docker builds](https://github.com/axllent/mailpit/actions/workflows/build-docker.yml/badge.svg)
![CodeQL](https://github.com/axllent/mailpit/actions/workflows/codeql-analysis.yml/badge.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/axllent/mailpit)](https://goreportcard.com/report/github.com/axllent/mailpit)

Mailpit is a small, fast, low memory, zero-dependency, multi-platform email testing tool & API for developers.

It acts as an SMTP server, provides a modern web interface to view & test captured emails, and contains an API for automated integration testing.

Mailpit was originally **inspired** by MailHog which is [no longer maintained](https://github.com/mailhog/MailHog/issues/442#issuecomment-1493415258) and hasn't seen active development for a few years now.

![Mailpit](https://raw.githubusercontent.com/axllent/mailpit/develop/docs/screenshot.png)


## Features

- Runs entirely from a single static binary
- SMTP server (default: `0.0.0.0:1025`)
- Web UI to view emails (formatted HTML, highlighted HTML source, text, headers, raw source, and MIME attachments including image thumbnails)
- HTML check to test & score mail client compatibility with HTML emails
- Link check to test message links (HTML & text) & linked images
- Screenshots of HTML messages via web UI ([see wiki](https://github.com/axllent/mailpit/wiki/HTML-screenshots))
- Mobile and tablet HTML preview toggle in desktop mode
- Light & dark web UI themes with auto-detect
- Advanced mail search ([see wiki](https://github.com/axllent/mailpit/wiki/Mail-search))
- Message tagging ([see wiki](https://github.com/axllent/mailpit/wiki/Tagging))
- Real-time web UI updates using web sockets for new mail
- Optional browser notifications for new mail (when accessed via either HTTPS or `localhost` only)
- Configurable automatic email pruning (default keeps the most recent 500 emails)
- Email storage either in a temporary or persistent database ([see wiki](https://github.com/axllent/mailpit/wiki/Email-storage))
- Fast SMTP processing & storing - approximately 70-100 emails per second depending on CPU, network speed & email size, easily handling tens of thousands of emails
- SMTP relaying / message release - relay messages via a different SMTP server including an optional allowlist of accepted recipients ([see wiki](https://github.com/axllent/mailpit/wiki/SMTP-relay))
- Optional SMTP with STARTTLS & SMTP authentication, including an "accept anything" mode ([see wiki](https://github.com/axllent/mailpit/wiki/SMTP-with-STARTTLS-and-authentication))
- Optional HTTPS for web UI ([see wiki](https://github.com/axllent/mailpit/wiki/HTTPS))
- Optional basic authentication for web UI ([see wiki](https://github.com/axllent/mailpit/wiki/Basic-authentication))
- A simple REST API ([see docs](docs/apiv1/README.md))
- Optional webhook for received messages ([see docs](https://github.com/axllent/mailpit/wiki/Webhook))
- Multi-architecture [Docker images](https://github.com/axllent/mailpit/wiki/Docker-images)


## Installation

The Mailpit web UI listens by default on `http://0.0.0.0:8025` and the SMTP port on `0.0.0.0:1025`.

Mailpit runs as a single binary and can be installed in different ways:


### Install via package managers

- **Mac**: `brew install mailpit` (to run automatically in the background: `brew services start mailpit`)
- **Arch Linux**: available in the AUR as `mailpit`
- **FreeBSD**: `pkg install mailpit`


### Install via bash script (Linux & Mac)

Linux & Mac users can install it directly to `/usr/local/bin/mailpit` with:

```bash
sudo bash < <(curl -sL https://raw.githubusercontent.com/axllent/mailpit/develop/install.sh)
```


### Download static binary (Windows, Linux and Mac)

Static binaries can always be found on the [releases](https://github.com/axllent/mailpit/releases/latest). The `mailpit` binary can be extracted and copied to your `$PATH`, or simply run as `./mailpit`.


### Docker

See [Docker instructions](https://github.com/axllent/mailpit/wiki/Docker-images) for 386, amd64 & arm64 images.


### Compile from source

To build Mailpit from source, see [Building from source](https://github.com/axllent/mailpit/wiki/Building-from-source).


## Usage

Run `mailpit -h` to see options. More information can be seen in [the docs](https://github.com/axllent/mailpit/wiki/Runtime-options).

If installed using homebrew, you may run `brew services start mailpit` to always run mailpit automatically.


### Testing Mailpit

Please refer to [the documentation](https://github.com/axllent/mailpit/wiki/Testing-Mailpit) on how to easily test email delivery to Mailpit.


### Configuring sendmail

Mailpit's SMTP server (default on port 1025), so you will likely need to configure your sending application to deliver mail via that port. A common MTA (Mail Transfer Agent) that delivers system emails to an SMTP server is `sendmail`, used by many applications, including PHP. Mailpit can also act as substitute for sendmail. For instructions on how to set this up, please refer to the [sendmail documentation](https://github.com/axllent/mailpit/wiki/Configuring-sendmail).
