Title: “Merge pull request” Considered Harmful
Date: 2014-08-25 05:28
Author: Tony
Slug: merge-pull-request-considered-harmful
Status: published

I've just finished re-reading Nathaniel Talbott's post, [“Merge pull request” Considered Harmful](http://blog.spreedly.com/2014/06/24/merge-pull-request-considered-harmful/#.U_smDrthWFA) and I'm in complete agreement. I'm not sure I'd like to use Hub though, as it ties things too closely to GitHub. I wonder if there's a good way, just using Git? What I ended up doing was:

> `git fetch https://github.com/sitaktif/pg8000.gitgit rebase FETCH_HEAD `

Then when I was happy I just did a `git push` as normal. Is this a good approach?

</p>

