# DualEntry

Ask your books questions in plain language.

This plugin connects to your live DualEntry ledger. Once you have signed in, you can find invoices and bills, see what has been paid, work through bank matches, and draft changes, all without writing a query.

## What you can do

- Find invoices, bills, journal entries, contracts, and fixed assets
- Look up the vendors, customers, accounts, companies, and items they belong to
- See related payments, what is still outstanding, and what changed
- Review DualEntry's bank-match suggestions and approve the ones that are right
- Build a record in conversation, check the values, then save

## Commands

| Command | What it does |
| --- | --- |
| `unpaid-invoices` | Outstanding invoices with an aging breakdown |
| `invoice-payments` | Every payment against a record, and what remains |
| `vendor-bills` | A vendor's open bills and total owed |
| `review-bank-matches` | Walk through suggested bank matches |

## Signing in

Your first DualEntry request opens a browser for DualEntry sign-in. Approve it once and the connection stays authorized.

There is no API key to create or paste. You see only the data your DualEntry account already permits, since the plugin does not widen your access.

## Nothing is saved without your say-so

Reading is free. Every change asks first.

Before any save, post, or delete, the plugin shows you the values and names the company the change will land in, then waits for your yes. You can preview a contract or fixed asset before creating it. If a change would touch a closed period, the plugin says so and stops.

## Network access

This plugin talks to one endpoint:

`https://api.dualentry.com/mcp/`

Authentication uses OAuth 2.1 with PKCE and dynamic client registration. The plugin reads no credentials from your machine and sends nothing anywhere else.

## Support

- MCP integration guide: https://docs.dualentry.com/developers/guides/mcp-integration
- Product: https://dualentry.com
- Email: support@dualentry.com

## License

The plugin code is [MIT](LICENSE). Use of the hosted MCP server is governed by DualEntry's terms.
