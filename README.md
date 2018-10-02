# Linaro Developer Cloud Website

Welcome to the official content repository for Linaro Developer Cloud's static [Jekyll](https://jekyllrb.com/) website.

We are open to you [submitting a PR](https://github.com/linaro/cloud/pulls) / [Issue](https://github.com/Linaro/cloud/issues/new) if there is anything you notice that is out of place or needs updating.

*****

## Adding Redirects to the Static site

We are using [Edge-rewrite](https://github.com/marksteele/edge-rewrite) which is a rewrite engine running in Lambda@Edge. The redirects are to be added to the `_data/routingrules.json` file in the webiste repository following the syntax rules [here](https://github.com/marksteele/edge-rewrite).

```
^/oldpath/(\\d*)/(.*)$ /newpath/$2/$1 [L]
!^/oldpath.*$ http://www.example.com [R=302,L,NC]
^/topsecret.*$ [F,L]
^/deadlink.*$ [G]
^/foo$ /bar [H=^baz\.com$]
```

__Note:__ These redirects are currently not respected by the link checker until built. So if trying to fix broken links by adding redirects then this may not be the best way to go about it currently. 