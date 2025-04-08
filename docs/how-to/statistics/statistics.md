# Collecting and Viewing Usage Statistics

There are several different ways you can set up Arca to collect usage statistics for you. Each work differently, and you may want to use all of them.

## Matomo

Matomo (formerly known as Piwik) is an open-source analytics platform. BC ELN hosts a Matomo instance at [https://analytics.bceln.ca](https://analytics.bceln.ca). 

Each new Arca site is set up to be tracked by Matomo when launched. 

Matomo reports can be accessed by logging into the [BC ELN Matomo site](https://analytics.bceln.ca). If you do not already have a login, contact the Arca Office to receive one.

The Matomo Reports module can display Matomo reports your the website itself, but cross-site-scripting security protocols currently make it unusable. Finding a way around this is in our longer-term plans.

## Google Analytics

If you want to use Google Analytics to track usage in Arca, you must first [set up your Google Analytics account](https://support.google.com/analytics/answer/9304153?hl=en).

When your account is set up, in your Arca site, enable the [Google Tag module](https://www.drupal.org/project/google_tag), and configure it (at `admin/config/services/google-tag`) with your Web Property ID.

## Drupal Statistics

Drupal's [Statistics module](https://www.drupal.org/project/statistics) has a very simple function: to count how many times a given node has been viewed. This is a running tally from the beginning of time (or, the installation of your website); it does not provide any nuance.

View counts are available at `admin/config/content/node-views-count-statistics`.