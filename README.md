# Readme

1. Configure the site according to your preferences - see [`siteConfig.js`](./content/_data/siteConfig.js) and template files.
2. Modify the list of feeds you want to aggregate - they are located in [`content/sites`](./content/sites/).
   1. Each site has the following properties:
      - `name` - name of the site
      - `url` - URL of the site
      - `avatar` - image to display alongside the site name (e.g. favicon). During the build process the image will be downloaded, resized and served locally
      - `feed` - URL of the RSS or JSON feed to fetch articles from
      - `hideFromSiteList` - set it to `true` if you want to hide this site from the list of sites on the Sites page. It is useful if you want to add two sites with different RSS feeds under the same name and avoid seeing duplicates on the list
3. Deploy the site to Netlify or Vercel
4. Set up the GitHub action in [`.github/workflows/scheduled_build.yml`](./.github/workflows/scheduled_build.yml):
   1. Create a build hook URL and save it as a GitHub secret in your repository - e.g. `NETLIFY_BUILD_HOOK_URL` or `VERCEL_BUILD_HOOK_URL`
5. Done! Your aggregator is up and running.

## Translation file

See [`phrases.js`](./content/_data/phrases.js) for the list of translatable static phrases.

## Note on persisting feed cache

The aggregator uses [eleventy-fetch](https://www.11ty.dev/docs/plugins/fetch/) plugin for fetching and caching network requests. If you use a hosting provider that supports persisting cache (e.g. Netlify or Vercel), you can limit number of network requests by making your `.cache` folder persistent between builds. See [Eleventy docs on how to set it up](https://www.11ty.dev/docs/deployment/#persisting-cache).
