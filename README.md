# ghcr.io/coolcow/ssh-localforward-configurator

Simple Docker image to generate SSH `LocalForward` configuration entries from a JSON services file.

---

## Usage

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

See `example.json` for the expected schema.
