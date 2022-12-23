# Ansible Builder - Execution Environment

# Ansible Builder

The current image is 10 months old and is release v1.0.0.  

1. Clone ansible/ansible-builder
1. Check out release 1.2.0 branch
1. Build the image
   ```bash
    podman build --rm \
        -t cloudera.com/ansible/ansible-builder:latest \
        -f Containerfile \
        .
   ```
1. (Push the image if not using locally)

# Build cldr-runner

(Assumes a minimal Ansible setup with `ansible-builder` installed in the `venv`.)

1. Build `cldr-runner`
   ```bash
   ansible-builder build \
      --rm \
      --file ee-example.yml \
      -t 'cloudera.com/cldr-runner:latest' \
      -v 3
   ```
1. (Push the iage if not using locally)

# Run the playbooks

This image is an [Execution Environment](https://ansible-builder.readthedocs.io/en/stable/definition/#) and can be used as the `provision-isolation` container or directly from within the container itself, such as

```bash
podman run -it cloudera.com/cldr-runner:latest /bin/bash  
```
