# Camli Blob Magic

[Note: not totally happy with this yet...]

Ideal Camli JSON blobs should begin with the following 15 bytes:

    {"camliVersion"

However, it's acknowledged that some JSON serialization libraries will format
things differently, so additional whitespace should be tolerated.

An ideal camli serializer will strive for the above header, though, by doing
something like:

- removing the "camliVersion" from the object, noting its value (and requiring
  it to be present)

- serializing the JSON with an existing JSON serialization library,

- removing the serialized JSON's leading "{" character and prepending the 15
  byte header above, as well as the colon and saved version and comma (which can
  have whitespace as desired)

