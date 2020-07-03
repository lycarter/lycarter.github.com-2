# Shutter Clicks

[![Netlify Status](https://api.netlify.com/api/v1/badges/de51fbac-26cb-4a06-9db5-dd0958fc3358/deploy-status)](https://app.netlify.com/sites/lycarter-blog/deploys)

## Tale

[![Gem Version](https://badge.fury.io/rb/tale.svg)](https://badge.fury.io/rb/tale)

Tale is a minimal Jekyll theme curated for storytellers. I'm using it for my Jekyll site.

## How to run

Install [Ruby](https://www.ruby-lang.org/en/) using [rbenv](https://github.com/rbenv/rbenv) (make sure to `rbenv global <version>`), then install [bundler](http://bundler.io/), and [Jekyll](https://jekyllrb.com/).
```bundle install```
```bundle exec jekyll serve --watch --drafts```

Debugging info is found at `/about-technical/`

## Netlify

- Install [netlify cli](https://docs.netlify.com/cli/get-started/)
- Install lm addon `netlify plugins:install netlify-lm-plugin && netlify lm:install`
- Add ca cert: `export NODE_EXTRA_CA_CERTS=/path/to/ca-bundle.crt`
- Login: `netlify login`
- Status: `netlify status`

After that, git lfs should mostly just work with netlify.

## Other notes

For setting page-specific sharing tags: https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md

For merging upstream master:

```
git remote add upstream git@github.com:chesterhow/tale.git
git fetch upstream
git merge upstream/master
```

For fixing git-lfs history:

```
$ git filter-branch --prune-empty --tree-filter '
git lfs track "*.jpg"
git lfs track "*.jpeg"
git lfs track "*.gif"
git lfs track "*.png"
git lfs track "*.pdf"
git add .gitattributes

git ls-files -z | xargs -0 git check-attr filter | grep "filter: lfs" | sed -E "s/(.*): filter: lfs/\1/" | tr "\n" "\0" | while read -r -d $'"'\0'"' file; do
    echo "Processing ${file}"

    git rm -f --cached "${file}"
    echo "Adding $file lfs style"
    git add "${file}"
done

' --tag-name-filter cat -- --all
```

## License
See [LICENSE](https://github.com/lycarter/lycarter.github.com/blob/master/LICENSE)
