# SOPS and age secrets encryption

## Requirements

- Mozilla SOPS: https://github.com/mozilla/sops
- age file encryption: https://github.com/FiloSottile/age

## Source

Original post: https://docs.technotim.live/posts/secret-encryption-sops/


## Encrypt:

### ENV
```
$ sops --encrypt --age age1d35nqlrcccdfzfzguekprn80p8vxkevvezmxhkrfp3w9vjqrnydsxs55s8 production.env > enc.production.env
```


### YAML

Only keys starting with `SECRET_` string will be encrypted.

```
$ sops --encrypt --encrypted-regex '^(SECRET_.*)$' --age age1d35nqlrcccdfzfzguekprn80p8vxkevvezmxhkrfp3w9vjqrnydsxs55s8 production.yaml > enc.production.yaml
```

## Decrypt:

### ENV
```
$ sops --decrypt --age age1d35nqlrcccdfzfzguekprn80p8vxkevvezmxhkrfp3w9vjqrnydsxs55s8 enc.production.env > dec.production.env
```

### YAML
```
$ sops --decrypt --age age1d35nqlrcccdfzfzguekprn80p8vxkevvezmxhkrfp3w9vjqrnydsxs55s8 enc.production.yaml > dec.production.yaml
```