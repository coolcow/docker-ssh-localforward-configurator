# ghcr.io/coolcow/ssh-localforward-configurator

A minimal Python-based Docker image that generates SSH `LocalForward` entries from a JSON services file.

The container runs `servicesToSshConf.py` directly. This project does not require the `docker-entrypoints` project.

---

## Usage

### Quick Start

```sh
docker run --rm ghcr.io/coolcow/ssh-localforward-configurator --help
```

### Generate SSH config from `example.json`

```sh
docker run --rm -i \
  -v "$(pwd)/example.json:/tmp/services.json:ro" \
  -v "$(pwd):/tmp/out" \
  ghcr.io/coolcow/ssh-localforward-configurator \
  /tmp/services.json \
  -n my-target \
  -t ssh.example.com \
  -p 22 \
  -u my-user \
  -o /tmp/out/ssh.config
```

The command writes SSH config output to the file passed via `-o` and prints matching `/etc/hosts` entries to stdout.

---

## Input format

The input must be a JSON array of services.

Each service object contains:

- `ip`: the remote service IP address
- `ports`: list of remote ports to forward
- `names`: list of host aliases

See `example.json` for a complete example.

---

## Local Testing

Run the built-in smoke tests locally.

1. `docker build -t ghcr.io/coolcow/ssh-localforward-configurator:local-test-build -f build/Dockerfile build`
2. `docker build --build-arg APP_IMAGE=ghcr.io/coolcow/ssh-localforward-configurator:local-test-build -f build/Dockerfile.test build`
