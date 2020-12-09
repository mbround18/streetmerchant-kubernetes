# Kubernetes Streetmerchant

Simple kubernetes deployment of streetmerchant.

**All credit for streetmerchant goes to: `https://github.com/jef/streetmerchant`**

## Usage

1. Have a kuberntes cluster running, I suggest `k3s.io`.
2. Have access to your cluster.
3. Create a env file at `./secrets/env.txt` based on `https://github.com/jef/streetmerchant/blob/main/.env-example`
4. Run `kubectl apply -k .` to stand this up.

## Testing your environment file

> Note: These have the `--cap-add=SYS_ADMIN` removed from the original command. This grants the docker container virtually root access to your host and should never be given to a docker container.

### Test run locally

```sh
docker run \
  -it --rm --env-file ./.env \
  ghcr.io/jef/streetmerchant:latest
```

### Testing notifications

```sh
docker run \
  -it --rm --env-file ./secrets/env.txt \
  ghcr.io/jef/streetmerchant:latest test:notification:production
```
