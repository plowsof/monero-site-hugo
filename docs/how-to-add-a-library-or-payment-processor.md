# How to Add a Library, Payment Processor or Tool

This guide explains how to list a developer library, a payment processor (or store plugin), a block explorer or another tool on the Tools pages, and how to add a merchant directory. Wallets and node software are listed on the Downloads page instead, see [How to Add a New Download Item](how-to-add-a-new-download-item.md).

## Where things are listed

| You are adding | Shown on | List in `src/data/` | Description key in `src/i18n/translations/<lang>/` |
| :--- | :--- | :--- | :--- |
| Developer library | `/resources/tools/develop/` | `resources/monero-tools.yaml`, `developerLibraries` | `tools.json`: `develop.tools.<id>` |
| Payment processor or store plugin | `/resources/tools/accept/` | `resources/monero-tools.yaml`, `paymentGateways` | `tools.json`: `accept.tools.<id>` |
| Block explorer | `/resources/tools/explore/` | `resources/monero-tools.yaml`, `blockExplorers` | `tools.json`: `explore.tools.blockExplorers.<id>` |
| Network tool | `/resources/tools/explore/` | `resources/monero-tools.yaml`, `networkTools` | `tools.json`: `explore.tools.network.<id>` |
| Utility | `/resources/tools/explore/` | `resources/monero-tools.yaml`, `utilities` | `tools.json`: `explore.tools.utilities.<id>` |
| Merchant directory | `/get-started/merchants/` | `get-started/merchants.yaml`, `merchants` | `merchants.json`: `subtitles.<id>` |

The number on each card of `/resources/tools/` counts the entries, so it updates by itself.

## Step 1: Add the logo (libraries, payment processors and merchant directories)

Put the logo in `src/assets/images/dev-tools/` (libraries), `src/assets/images/payment-gateways/` (payment processors) or `src/assets/images/directories/` (merchant directories). Use a square image, 256×256 pixels or larger, like the existing logos; PNG, WebP or AVIF. The build resizes it. Explorers, network tools and utilities have no logo.

## Step 2: Add the entry

Add an item to the list. A library, in `src/data/resources/monero-tools.yaml`:

```yaml
developerLibraries:
  # ...existing entries...
  - id: moneroRust
    title: monero-rust
    href: "https://github.com/example/monero-rust"
    logo: images/dev-tools/monero-rust.png
```

A payment processor is the same, under `paymentGateways`, with its logo in `images/payment-gateways/`.

Notes:
- `id` must be unique in its list, in camelCase. It is the key of the description (step 3).
- `title` is the name as the project writes it.
- `href` is a full URL (include `https://`).
- `logo` is the image's path inside `src/assets/`.
- Optional, for explorers, network tools and utilities only: `onionHref`, the project's Tor (.onion) address, shown as an extra link.
- The entries are shown in the order of the file.

A merchant directory, in `src/data/get-started/merchants.yaml`, uses `name`, `link` and `onionLink` instead (it is sorted by name):

```yaml
merchants:
  # ...existing entries...
  - id: myDirectory
    name: My Directory
    logo: images/directories/my-directory.png
    link: "https://mydirectory.example"
```

## Step 3: Add the description

Each entry's one-line description is a translation string, so it can be translated on Weblate. Add it in English to `src/i18n/translations/en/tools.json` (or `merchants.json`), at the key from the table:

```json
{
    "develop": {
        "tools": {
            "moneroRust": "Rust library for Monero wallets and RPC"
        }
    }
}
```

Only edit the English file: translators add the other languages on Weblate, and until they do, those languages show the English text.

## Testing

- Run `hugo server` and open the page from the table (for example `http://localhost:1313/resources/tools/develop/`).
- Check the logo shows, the title and description are right, and the link opens the project.
- If the description shows as a key (like `develop.tools.moneroRust`) instead of text, the `id` and the description key don't match.

## PR checklist

- [ ] The project is open source or otherwise trustworthy enough to be recommended to users, is actively maintained and supports Monero.
- [ ] Logo added (if the list has logos) and referenced from the entry.
- [ ] Entry added to the right list in `src/data/`, with a unique `id`.
- [ ] English description added at the matching key.
- [ ] Checked the page with `hugo server`.
- [ ] Open a PR saying what the project is and linking to it.
