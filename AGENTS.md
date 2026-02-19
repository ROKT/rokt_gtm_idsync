# rokt_gtm_idsync

## Project Overview

This repository contains the **mParticle by Rokt — IDSync Template** for Google Tag Manager (GTM). It is a public GTM Community Template Gallery submission that enables partners to perform identity sync operations (identify, login, logout, modify) via the mParticle SDK through Google Tag Manager.

**Resident Expert:** Alex Sapountzis (alex.sapountzis@rokt.com)

## Architecture

This is a single-file GTM custom tag template (`.tpl`), not a traditional application. The template:

1. Reads an `identityCallback` function and `userIdentities` object from the GTM data layer.
2. Constructs an identity request based on the configured event type.
3. Calls the appropriate mParticle Identity API method (`identify`, `login`, `logout`, or `modify`) via `callInWindow`.
4. Pushes a `roktIdSyncComplete` event to the data layer on completion.

The template requires the mParticle SDK to be loaded on the page before this tag fires (typically via a separate GTM tag).

## Tech Stack

- **Language:** Google Tag Manager Sandboxed JavaScript
- **Platform:** Google Tag Manager (Web container)
- **SDK Dependency:** mParticle Web SDK (must be loaded separately)
- **License:** Apache 2.0

## Development Guide

### Prerequisites

- A Google Tag Manager account
- Access to the [GTM Community Template Gallery](https://tagmanager.google.com/gallery/#/?page=1)
- The mParticle SDK loaded on the target site

### Working with the Template

The entire template logic is in `template.tpl`. This file follows the [GTM custom template format](https://developers.google.com/tag-platform/tag-manager/templates) and contains:

- `___INFO___` — Template metadata (name, categories, description)
- `___TEMPLATE_PARAMETERS___` — UI configuration fields (event type selector, identity option fields)
- `___SANDBOXED_JS_FOR_WEB_TEMPLATE___` — The runtime JavaScript logic
- `___WEB_PERMISSIONS___` — Required GTM permissions (logging, globals access, data layer read)
- `___TESTS___` — Built-in test scenarios

### Testing

Follow the [GTM Wrapper testing guide](https://github.com/ROKT/gtm_wrapper/tree/master/docs/guides/how-to-test.md) to set up the Testing Playground and test template changes.

### Ad-Hoc Usage

Download the `.tpl` file and upload it in your Google Tag Manager Template interface. See [GTM template docs](https://developers.google.com/tag-platform/tag-manager/templates) for details.

## Deployment Process

Follow [Google's template update instructions](https://developers.google.com/tag-platform/tag-manager/templates/gallery#update_your_template) to deploy the template to the GTM Community Template Gallery.

## Project Structure

| Path | Description |
|---|---|
| `template.tpl` | GTM custom tag template (metadata, parameters, sandboxed JS, permissions, tests) |
| `metadata.yaml` | Template version history and homepage/documentation links for the GTM Gallery |
| `README.md` | Usage instructions and setup guide |
| `LICENSE` | Apache 2.0 license |

## Template Configuration

The tag exposes the following configurable parameters:

| Parameter | Description |
|---|---|
| **IDSync Event Type** | Select one of: Identify, Login, Logout, Modify |
| **Identify Options** (shown only for Identify events) | Email, Customer ID, Mobile Number, Phone Number 2/3, Facebook, Facebook Custom Audience ID, Google, Twitter, Microsoft, Yahoo, Other 1–10 |

## Version History

| Version | Change |
|---|---|
| Initial | Initial Release |
| 2 | Add Identify event |
| 3 | Updated Identity UserIdentities |
| 4 | Added `roktIdSyncComplete` event to data layer |

## Maintaining This Document

When making changes to this repository that affect the information documented here
(template parameters, deployment process, architecture, etc.),
please update this document to keep it accurate. This file is the primary reference
for AI coding assistants working in this codebase.
