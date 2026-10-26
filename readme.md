# winn-apps.uk

Website for Andrew Winn's apps, hosted on the Azure Static Web App **andrewwinn**
(https://thankful-tree-098e32203.6.azurestaticapps.net, to become https://winn-apps.uk).

## Layout

| Path | Page |
|---|---|
| `site/index.html` | Home: a card per app |
| `site/limitalert/` | LimitAlert: pitch, screenshots, features, pricing |
| `site/limitalert/privacy/` | LimitAlert privacy policy (App Store Connect Privacy Policy URL) |
| `site/limitalert/support/` | LimitAlert support and FAQ (App Store Connect Support URL) |
| `site/.well-known/appspecific/com.tesla.3p.public-key.pem` | Tesla Fleet API public key (must stay at this path) |
| `site/assets/` | `site.css` (shared styles) and per-app images |
| `site/staticwebapp.config.json` | Azure settings: `/privacy` and `/support` short links, 404 page, headers |

Plain HTML and CSS, no build step. Preview locally with `python3 -m http.server 8090 --directory site`.

## Publishing

Every push to `main` runs `.github/workflows/deploy.yml`, which uploads `site/` to the Static Web App. It needs the
repository secret `AZURE_STATIC_WEB_APPS_API_TOKEN` (Azure › andrewwinn › Overview › Manage deployment token).

`vue-app/`, `infra/` and `azure.yaml` are the original `azd` starter; they can go once the new site is live.

## Adding an app

Copy `site/limitalert/` to `site/<app>/`, put its images in `site/assets/<app>/`, and add a card to `site/index.html`.
