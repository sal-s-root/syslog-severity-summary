# syslog-severity-summary

Decode syslog priority numbers into facility and severity counts.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "priorities": [
    13,
    14,
    13
  ]
}
```

Result:

```json
{
  "severities": {
    "5": 2,
    "6": 1
  },
  "facilities": {
    "1": 3
  }
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Uses numeric syslog priority values; does not parse timestamps, hostnames, or transport framing.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [dns-record-linter](https://github.com/sal-s-root/dns-record-linter), [route-longest-prefix](https://github.com/sal-s-root/route-longest-prefix).

## Project status

A small standalone learning exercise using supplied fixtures. The related
[infrastructure toolbox](https://github.com/sal-s-root/infra-toolbox) collects these
checks in one place.

The assigned historical dates form a retrospective learning schedule; this
exercise was created or reconstructed in 2026. See [history and scope](HISTORY.md).
