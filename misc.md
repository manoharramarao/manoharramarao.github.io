# Random items

## Self signed certificate error on nodejs.org

### Yarn install throws error with self signed certificate in certificate chain

set NODE_TLS_REJECT_UNAUTHORIZED to 0 before running yarn install

```bash
$ export NODE_TLS_REJECT_UNAUTHORIZED=0
$ yarn install
```

> 
> 
> This is not safe. This turns off TLS validation
> 
> 
