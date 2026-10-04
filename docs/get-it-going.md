# get it going

## Required versions

- Python: 3.8.x (*[Pillow 7 does not support Python 3.9](https://stackoverflow.com/questions/60590809/cannot-pip-install-pillow-7-on-python-3-9)*)
- MongoDB: 4.x (*TODO higher versions? 9.x might still work*)
- Redis: any? confirmed working in 8.10.2
- A C Compiler
- An installation of [uv](https://docs.astral.sh/uv/)
- Potentially an installation of `libcrypt`. `libxcrypt` worked for me.

All dependencies have been locked to ancient versions, just prior to repo archiving.

## Setup

1. Clone this repository.
2. Run `uv sync`. Good luck.
3. Start MongoDB **without** authentication; I used [dubc's mongodb-4.0 Docker image.](https://hub.docker.com/r/dubc/mongodb-4.0)
4. Start Redis.
5. Fill out the `config.py.example`, and rename it to `config.py`.
6. Run the bot with `uv run main.py`; It should start up just fine.

## Configuration

### `COG_BLACKLIST`

TODO: A blacklist?

### `DEBUG_WEBHOOK`

A Discord webhook which sends valuable debug informations.

### `MONGODB_HOST`

The host of the MongoDB server.

Example: `localhost`

### `MONGODB_USER`

The username for MongoDB user; **does not apply in "beta" cluster**

Example: `abyss`

### `MONGODB_PASS`

The password for MongoDB user; **does not apply in "beta" cluster**

Example: `"hunter2"`

### `MONGODB_DBSE`

The authSource option. Usually `admin`. **does not apply in "beta" cluster**

Example: `"admin"`

### `OWNERS`

A list of user IDs, refer [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID) for how to get an user's User ID.

> [!WARNING]
> Owners allow the user to execute **arbitary code**.
> I recommend against adding anyone here if you do not understand what this means.

Example: `[ 991635724958965840 ]`

### `REDIS`

Arguments to be passed to initialize Redis.

Refer [here](https://aioredis.readthedocs.io/en/v1.3.0/api_reference.html#aioredis.create_redis_pool) for all possible keys.

Example: `{"address": ("localhost",6379)}`

### `SPLASHES`

List of splash texts, that will be picked at random for `launcher.py`.

Example: `["Kenji, you're gonna eat anything besides ramen or what?"]`

### `TICK_YES`

An emoji to use for "Yes" reaction.

### `TICK_NO`

An emoji to use for "No" reaction.

### `TOKEN`

The Discord token.

## Troubleshooting

### "unable to get local issuer certificate"... SSL error

`export SSL_CERT_FILE=$(python -m certifi)` if on \*nix,

`setx SSL_CERT_FILE (python -m certifi)` on powershell,

`for /f "delims=" %a in ('python -m certifi') do @set SSL_CERT_FILE=%a` on cmd i believe? *(untested)*


```

$ docker run -p 27017:27017 -p 28017:28017 --rm -e AUTH=no dubc/mongodb-4.0
$ docker run --rm -d -p 6379:6379 redis

```
