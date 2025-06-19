# Remote and Embedded Media

It is possible to include remotely-hosted media in your Islandora repository. This media gets embedded in your Repository Item node page, the same as any media that is stored directly in the repository.

There are three ways to do this: the included-with-drupal Remote Video option (which only works for YouTube and Vimeo links), with a link to the item in an oEmbed-enabled platform, and with embed code.

## Remote Video

Drupal includes a Remote Video media type, which supports embedded videos by linking to videos hosted on YouTube or Vimeo. Choose this option only if your media is hosted in one of those two sites.

1. At the host website (YouTube or Video), find your video, and click the Share button. Copy the link it provides.
2. Create your Repository Item as normal. Make sure "Add media" is selected.
3. At the Media screen, choose `Remote video`.
4. In the `Video URL` field, paste the link provided by YouTube/Vimeo.
5. Under `Media Use`, select "Service file".
6. Save.

## oEmbed links

The oEmbed Remote Media option uses the same standard as Remote Video (oEmbed), but with a much wider range of providers. Your media does not have to be a video - it could be audio, an image, even a tweet. A link to the item is all that's required.

By default, any [officially-listed oEmbed providers](https://oembed.com/providers.json) are  supported with this media type. If your provider is not in that list, you may be able to add it as a custom provider.

1. Copy the link to your remote media item from its host website.
2. Create your Repository Item as normal. Make sure "Add media" is selected.
    - Under Content Type, choose "video" or "audio" as appropriate.
3. At the Media screen, choose `oEmbed Remote Media`.
4. In the URL field, paste your link.
5. Under `Media Use`, select "Service File".
6. Save.

### Adding new oEmbed providers

If your provider is oEmbed-capable but is not in the list of available providers, contact the Arca Office to get your provider added to the list as a Custom Provider.

Provide the following information:

- Provider name
- Provider URL
- All Endpoints and relevant information:
  - Endpoint schemes:
    - URLs from a provider that may have an embedded representation. E.g. `http://custom-provider.example.com/id/*`, `https://custom-provider.example.com/id/*`
  - Endpoint URL:
    - A URL where the consumer can request representations for scheme URLs. E.g. `https://custom-provider.example.com/api/v2/oembed/`
  - Discovery: Whether or not a provider supports discoverability of supported formats
  - Supported formats (XML, JSON, or both)
  - A link to a sample object at the provider's site so we can confirm your info works
  
If you do not have this information, contact the provider's helpdesk to obtain it.

If your media source is not oEmbed-compatible, you can use the Embed Code approach.

## Embed Code

The Embed Code approach is similar to how Remote Media objects were handled in Islandora 7: copy the embed code provided by the remote host, and paste it into the repository.

This also works for local HTML content that is not remotely hosted. The content will render when viewing the Repository Item.

1. Create your Repository Item as normal. Make sure "Add media" is selected.
2. At the Media screen, choose `Embed Code`.
3. Fill out the fields:
  - Give your media an appropriate title
  - In the `Insert Embed Code` field, simply paste the embed code as provided by the host website.
4. Under Media Use, make sure "Service File" is selected.
5. Save.