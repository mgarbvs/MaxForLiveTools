# MaxForLiveTools

Utilities for building and working with Max for Live devices from the command line.

## Tools

### `build_amxd.py`

Assembles a `.maxpat` JSON file into a `.amxd` device file without opening Max/Live.

The `.amxd` format is a 32-byte binary header followed by the raw `.maxpat` JSON. This script constructs that header and writes the final device file.

**Usage:**

```bash
python3 build_amxd.py source.maxpat dest.amxd
```

**Notes:**

- Warns if the `.maxpat` contains an empty `parameterbanks` block, which causes a NULL dereference crash in Live/Max when loading devices with `live.*` parameters. Remove the top-level `parameters` key from the `.maxpat` to avoid this.
- No compression is applied — the JSON is written verbatim.

## Requirements

- Python 3
