# Upload posts from Goodreads to Tumblr (UploadPosts.py)

UploadPosts.py has a few hardcoded variables in it which you can set your own tumblr's stuff. The script parses the same data the analysis below uses - go [here](https://www.goodreads.com/review/import) and press "Export your library" to get your own csv.

## Dependencies

    pytumblr
    pandas

Should be just

    sudo pip install pytumblr pandas

## What it does

This script will upload the 30 last reviews it gets from the Goodreads API and puts them on the tumblr 'queue' - by default tumblr posts two posts per day from the queue. It also cleans up a few things - Goodreads specific links in the review text, unicode author and book titles, etc.

It will print something like:

    INFO:root:Uploading post for Die Ausgewanderten
    INFO:root:Uploading post for Slimer
    INFO:root:Uploading post for Never Split the Difference: Negotiating As If Your Life Depended On It
    INFO:root:Uploading post for Naked Statistics: Stripping the Dread from the Data
    INFO:root:Uploading post for King Lear
    INFO:root:Uploading post for Hamlet


And then you have 30 posts in your queue.

To set it up go to https://www.tumblr.com/settings/apps and create an app, or copy OAuth Consumer Key and OAuth Consumer Secret. Then go to https://api.tumblr.com/console/calls/user/info and enter those to receive TOKEN and TOKEN_SECRET, and enter those in the script.

After that it's just a matter of running the script:

    python UploadPosts.py goodreads_export.csv CREDENTIALS --blogname potatoHero

It does not support Python 3 since the pytumblr library works only under Python 2.
