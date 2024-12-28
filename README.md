# bluesky-firehose Python Library

Just a very lightweight wrapper around the Bluesky Firehose API, i.e. you don't need any credentials
to access Bluesky. For obvious reasons, this does not return content that is not public, and 
does not enable you to send posts. 

Based on https://github.com/ten-faced-carrot/bluesky-python

############### STILL NEEDS TO BE DONE! #####################

The original bluesky-python wrapper does not use the atproto library. 
So my fist decision would be: use the atproto API, or emulate it. 

Reading from the firehose via atproto works like this: 
```py
client = Client(base_url="https://api.bsky.app")
profile = client.app.bsky.actor.get_profile({'actor': handle})
```

This wouldn't be that different from the code below, only replacing ```clent.get_profile()``` with
```client.app.bsky.actor.get_profile()```. So it's probably not worth it. Leaving the notes in the repo
anyway, so I won't have to look it up again. 

### Example

```py
from blueskyfirehose import BlueskyBasicClient

client = BlueskyFirehoseClient()
# client = BlueskyBasicClient.from_login_data("example.bsky.social", "1234567890")

profile = client.get_profile(BLUESKY_HANDLE)
print("Profile Information:")
print(f"Handle: {profile['handle']}")
print(f"Display Name: {profile['displayName']}")
print(f"Description: {profile['description']}")
print(f"Followers Count: {profile['followersCount']}")
print(f"Follows Count: {profile['followsCount']}")
print(f"Posts Count: {profile['postsCount']}")
```