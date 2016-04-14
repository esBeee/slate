# Localization

To request the response to be in a certain language, set the value of *Accept-Language* in your request header to a comma separated list of <a href='https://en.wikipedia.org/wiki/IETF_language_tag'>IETF language tags</a> (for example *en, en-US, en-cockney*). The API will then select the last tag (from left to right), that is supported. Currently supported are

### Registered locales

IETF language tag | Description
----------------- | -----------
en | English (default)
de | German

<aside class="success">
Each response contains a value for *Content-Language* in the header that holds the language tag that was set before creating the messages.
</aside>

<aside class="warning">
If none of the tags stated in the *Accept-Language* key in your request header is registered, the response will be in english.
</aside>

<aside class="notice">
If no *Accept-Language* key was set in your request header, the response will be in english.
</aside>

<aside class="notice">
As of now, this only refers to detailed error messages and notifications.
</aside>
