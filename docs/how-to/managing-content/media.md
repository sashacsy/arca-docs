# Managing Islandora Media

This document is under construction. For a detailed explanation of how media works in Islandora, [see the Islandora Wiki](https://islandora.github.io/documentation/user-documentation/media/). (Note that we do not use Fedora, so ignore those parts.)

Special media types in Arca:

- oEmbed Remote Media: Takes a URL to a remotely hosted media object from any oEmbed-compatible source, and displays it as an embedded object in the repository. This for the most part is how re replicate the old Islandora Remote Media Solution Pack.
    - Works with the most common media sources, such as YouTube, Vimeo, Hulu, SoundCloud, and even Twitter, Bluesky, and Reddit posts.
    - You can also configure the oEmbed Providers module to add additional custom sources, such as your Kaltura endpoint. (Documentation for this to come.)
    