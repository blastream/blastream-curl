Some examples from : https://api.v2.blastream.com/api-docs/

## Create a channel and an admin access of the channel

### Curl request

```firstchannel``` is the name of your channel

```sh
curl -X 'POST' \
  'https://api.v2.blastream.com/space/channel/firstchannel' \
  -H 'accept: application/json' \
  -H 'X-Api-Public: PUBLIC_KEY_API' \
  -H 'X-Api-Private: PRIVATE_KEY_API' \
  -H 'Content-Type: application/json' \
  -d '{
  "plan": "pro1",
  "billing": "hourly"
}'
```

### Curl response

```json
{
  "token": "SESSION_ADMIN_TOKEN",
  "url": "//app.v2.blastream.com/eve_firstchannel",
  "id": 26712,
  "prefix": "eve",
  "justBeenCreated": false
}
```

### Iframe url build

```reponse->url ? token=SESSION_ADMIN_TOKEN & api=PUBLIC_KEY_API```

```https://app.v2.blastream.com/eve_firstchannel?token=SESSION_ADMIN_TOKEN&api=PUBLIC_KEY_API```

## Create a participant

### Curl request

```sh
curl -X 'POST' \
  'https://api.v2.blastream.com/space/channel/firstchannel/participant' \
  -H 'accept: application/json' \
  -H 'X-Api-Public: PUBLIC_KEY_API' \
  -H 'X-Api-Private: PRIVATE_KEY_API' \
  -H 'Content-Type: application/json' \
  -d '{
  "nickname": "nickname of viewer",
  "id": "your_platform_id"
}'
```

### Curl response

```json
{
  "token": "SESSION_TOKEN",
  "url": "https://app.v2.blastream.com/eve_firstchannel"
}
```

### Iframe url build

```reponse->url ? token=SESSION_TOKEN & api=PUBLIC_KEY_API```

```https://app.v2.blastream.com/eve_firstchannel?token=SESSION_TOKEN&api=PUBLIC_KEY_API```

## Create a collborator

```sh
curl -X 'PUT' \
  'https://api.v2.blastream.com/channel/collaborator' \
  -H 'accept: application/json' \
  -H 'X-Auth-Token: SESSION_ADMIN_TOKEN ' \
  -H 'Content-Type: application/json' \
  -d '{
  "displayname": "my animator",
  "status": "animator"
}'
```

### Curl response

```json
{
  "token": "COLLAB_TOKEN",
  "invite_link": "https://app.v2.blastream.com/eve_firstchannel/access/COLLAB_TOKEN"
}
```

### Iframe url build

```reponse->invite_link ? api=PUBLIC_KEY_API```

```https://app.v2.blastream.com/eve_firstchannel/access/COLLAB_TOKEN?api=PUBLIC_KEY_API```
