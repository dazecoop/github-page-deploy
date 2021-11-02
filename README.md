# Deploy Vue.js app to GitHub pages

Original source: https://blog.logrocket.com/build-deploy-vue-js-app-github-pages/

1. Follow above tutorial, probably. But TL;DR
2. Integrate source folders/files with your app
3. Modify [scripts/gh-pages-deploy.js](https://github.com/dazecoop/github-page-deploy/blob/main/scripts/gh-pages-deploy.js#L9) with your project name
4. Commit & push to your `master` branch
5. Run `npm run deploy` to deploy to GitHub pages

## 🤨 What's different compared to LogRocket guide?
GitHub doesn't support history mode in Vue.js within GitHub pages, so a workaround was to manually set this to `mode: 'hash'` within my project. The impact of this was hash mode was used everywhere, including on Prod. Not ideal. My modified `gh-pages-deploy.js` script [finds/replaces this automatically](https://github.com/dazecoop/github-page-deploy/blob/main/scripts/gh-pages-deploy.js#L31) prior to deploying to GitHub pages upon the `npm run deploy` command.

Secondly, as per guide above, a `vue.config.js` file is required along with setting a `publicPath` matching your GitHub pages project name. The impact was this was also affecting Prod as well. So as per above, my modified script also finds/replaces for you automatically.

Don't worry, the find/replaces are also [automatically reverted back](https://github.com/dazecoop/github-page-deploy/blob/main/scripts/gh-pages-deploy.js#L57) upon a successful deploy 😉
