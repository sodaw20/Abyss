# Clusters

TODO: 
from cogs/midnight.py; "beta" is testing bot, "Beta" is cluster #2

## "beta" cluster

When bot is instantiated not through `launcher.py` (i.e. `uv run main.py`), It runs as the "beta" cluster.

It causes the prefix to be "beta$ ", and **not authenticate on MongoDB**. It also ignores commands from anyone besides in the `config.OWNERS` key.
