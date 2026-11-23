# hugolify-theme-places

## Install

Edit `config/_default/module.yaml` to install the `hugolify-theme-places` module:

### V2

```yml
imports:
  - path: github.com/hugolify/hugolify-theme-places/v2
  - path: github.com/hugolify/hugolify-theme/v2
```

### V1

```yml
imports:
  - path: github.com/hugolify/hugolify-theme-places
  - path: github.com/hugolify/hugolify-theme
```

## vCard

Each place page publishes a vCard (`.vcf`) next to it, named after the page slug, e.g. `/places/paris-office/paris-office.vcf`.
It is built from `title`, `company`, `address` (street, city, region, zipcode, country, map pin) and `contact` (`phone`, `fax`, `email`).

The download link is added to the contact list of the place page by
`places/contact/vcard.html`, the hook `commons/contact/contacts.html` looks for.
Nothing to wire.

To place it somewhere else, render it from the resource:

```go-html-template
{{ with partial "places/vcard.html" . }}
  {{ partial "commons/contact/vcard.html" . }}
{{ end }}
```

Options, in `config/_default/params.yaml`:

```yml
places:
  vcard:
    enable: true
    organization: '' # ORG field when the place has no company, defaults to the site title
```

## Documentation

https://www.hugolify.io/docs/

## Licensing

Hugolify is free for personal or commercial projects (MIT license)
