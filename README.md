# yarn vs npm

This is hardly scientific comparison done on the following machine with typical daily workload.

#### Machine

```
Model Name: MacBook Pro
Model Identifier: MacBookPro16,1
Processor Name: 8-Core Intel Core i9
Processor Speed: 2.4 GHz
Number of Processors: 1
Total Number of Cores: 8
L2 Cache (per Core): 256 KB
L3 Cache: 16 MB
Hyper-Threading Technology: Enabled
Memory: 32 GB
```

#### Versions

```
❯ node --version
v15.4.0

❯ yarn --version
1.22.10

❯ npm --version
7.0.15
```

## yarn

#### clean

`rm yarn.lock && rm -rf node_modules && yarn cache clean && time yarn`

Run 1: `=> yarn 18.61s user 16.73s system 144% cpu 24.526 total`
Run 2: `=> yarn 10.39s user 9.28s system 127% cpu 15.472 total`
Run 3: `=> yarn 18.32s user 17.20s system 164% cpu 21.553 total`
Run 4: `=> yarn 18.21s user 16.91s system 164% cpu 21.324 total`

#### cached

`rm -rf node_modules && time yarn`

Run 1: `=> yarn 8.77s user 10.10s system 230% cpu 8.182 total`
Run 2: `=> yarn 8.22s user 8.82s system 233% cpu 7.299 total`
Run 3: `=> yarn 8.18s user 8.91s system 229% cpu 7.448 total`
Run 4: `=> yarn 8.60s user 9.72s system 256% cpu 7.148 total`

## npm

### with `--force`

#### clean

`rm package-lock.json && rm -rf node_modules && npm cache clean --force && time npm install --force`

Run 1: `=> npm install --force 57.76s user 21.36s system 135% cpu 58.284 total`
Run 2: `=> npm install --force 57.41s user 20.69s system 145% cpu 53.592 total`
Run 3: `=> npm install --force 59.05s user 21.85s system 141% cpu 57.017 total`
Run 4: `=> npm install --force 58.57s user 21.72s system 142% cpu 56.157 total`

#### cached

`rm -rf node_modules && time npm install --force`

Run 1: `=> npm install --force 41.08s user 19.91s system 125% cpu 48.744 total`
Run 2: `=> npm install --force 21.21s user 16.19s system 217% cpu 17.175 total`
Run 3: `=> npm install --force 21.27s user 15.95s system 222% cpu 16.728 total`
Run 4: `=> npm install --force 39.72s user 19.84s system 133% cpu 44.555 total`
Run 5: `=> npm install --force 22.52s user 16.34s system 216% cpu 17.935 total`
Run 6: `=> npm install --force 21.03s user 16.10s system 221% cpu 16.793 total`

> Ran it twice more due to these odd spikes.

### with `--legacy-peer-deps`

#### clean

`rm package-lock.json && rm -rf node_modules && npm cache clean --force && time npm install --legacy-peer-deps`

Run 1: `=> npm install --legacy-peer-deps 35.73s user 13.33s system 125% cpu 38.946 total`
Run 2: `=> npm install --legacy-peer-deps 36.25s user 13.40s system 128% cpu 38.534 total`
Run 3: `=> npm install --legacy-peer-deps 35.35s user 12.97s system 126% cpu 38.327 total`
Run 4: `=> npm install --legacy-peer-deps 35.70s user 14.06s system 126% cpu 39.297 total`

#### cached

`rm -rf node_modules && time npm install --legacy-peer-deps`

Run 1: `=> npm install --legacy-peer-deps 13.36s user 10.24s system 172% cpu 13.680 total`
Run 2: `=> npm install --legacy-peer-deps 12.58s user 9.49s system 179% cpu 12.317 total`
Run 3: `=> npm install --legacy-peer-deps 12.65s user 9.38s system 177% cpu 12.420 total`
Run 4: `=> npm install --legacy-peer-deps 13.74s user 10.01s system 167% cpu 14.188 total`
