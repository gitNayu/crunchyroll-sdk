<p align="center">
    <a href="https://github.com/gitNayu/crunchyroll-sdk">
        <img src="https://raw.githubusercontent.com/gitNayu/crunchyroll-sdk/main/assets/banner.png" alt="Crunchyroll SDK">
    </a>
</p>

# Unofficial Crunchyroll SDK

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat)](LICENSE)
[![Python Client](https://img.shields.io/badge/Python%20Client-3776AB?style=flat&logo=python&logoColor=white)](https://github.com/gitNayu/cr-client-py)

###### Unofficial, open-source SDK implementations for Crunchyroll.

An independent project providing unofficial Crunchyroll API client implementations in multiple programming languages. Designed to make Crunchyroll's API functionality accessible to developers building their own applications, tools, and integrations.

## Why Crunchyroll SDK?

Interacting with an API directly often means repeatedly implementing authentication, HTTP requests, response parsing, and error handling.

Crunchyroll SDK aims to simplify this process by providing reusable, open-source client implementations that handle these details for you.

- **Easy integration** – Use existing client functionality instead of implementing API interactions from scratch.
- **Structured data** – Work with organized API responses.
- **Multiple languages** – Choose an implementation that fits your development environment.
- **Flexible usage** – Integrate the clients into your own applications and workflows.
- **Open source** – Inspect, modify, and contribute to the implementations.
- **Developer-focused** – Spend less time implementing API interactions and more time building your application.

## Disclaimer

This is an independent, **unofficial project**. It is not affiliated with, endorsed by, or associated with *Crunchyroll, LLC*.

Crunchyroll is a trademark of its respective owner.

### Third-Party Usage and Responsibility

This project is provided as an unofficial API SDK for development, interoperability, and independent application integrations.

I do not endorse, support, maintain, or take responsibility for third-party repositories, applications, or modifications that use these clients to download, redistribute, or otherwise obtain Crunchyroll content without authorization.

The existence of this SDK does not imply approval of such projects or their functionality. Third-party developers are solely responsible for their own implementations and how they use this software.

I reserve the right to distance this project from third-party uses that conflict with its intended purpose.

## Client Implementations

### Python Client

The Python implementation is the primary reference client.

**Repository:** [gitNayu/cr-client-py](https://github.com/gitNayu/cr-client-py)

#### Installation

```bash
git clone https://github.com/gitNayu/cr-client-py.git
cd cr-client-py
pip install .
```

### TypeScript Client

Coming soon.

## Authentication and Authorization

**This project does not ship any keys, secrets, tokens, or other authorization data.** You must provide your own.

- No client keys or client secrets are included in this repository.
- No account logins or tokens are included.
- You are responsible for obtaining and using your own credentials in accordance with the service's terms.

#### Setup

1. Copy `.env.example` to `keys.env`.
2. Add one line per client, in this format:

   ```
   NAME=base64(key:secret)
   ```

   `NAME` can be any name you choose.

3. Set `ACTIVE` to the name of the key you want to use.

Example `keys.env` (fake values):

```env
ACTIVE=ANDROID_TV
ANDROID_TV=a2V5OnNlY3JldA==
ANDROID_PHONE=b3RoZXJrZXk6b3RoZXJzZWNyZXQ=
```

To generate the Base64 value:

```bash
python3 -c "import base64; print(base64.b64encode(b'key:secret').decode())"
```

Never commit `keys.env`. It is listed in `.gitignore`. Base64 is not encryption, so keep the file private.

## Quick Start

```python
from crunchyroll_client import Client

cr = Client()  # no account needed

# 1. Search
hits, key = cr.search('Spy x Family')
series_id = hits[0]['id']

# 2. Get all metadata (every language)
meta, key = cr.get_series_metadata(series_id, episodes=False)
print(meta['localized']['en-US']['title'])

# 3. Get image URLs
urls, key = cr.get_image_urls(meta)
print(urls['images'].get('poster_tall'))

# 4. See which client key was used
print(key.label)
```

Every function returns `(data, key)`. The SDK only returns data and URLs. It does not save files or download images.

## Contact Information

**E-mail:**

- [mail.nayu@proton.me](mailto:mail.nayu@proton.me)
