[Warp](https://developers.cloudflare.com/warp-client/get-started/linux/)

a tool to change your that hides your DNS, it is similar to a vpn.

in arch you need the [AUR](https://aur.archlinux.org/packages/cloudflare-warp-bin)

we also need to enable or lunch the service 

```zsh
sudo systemctl enable --now warp-svc.service
```

this however will keep it running in the background so you need to disable it later.

## start/stop the service 

We can simply run the app in the background without enable it

```zsh
sudo systemctl start wrap-svc
```

Then we need to `stop` it when we are done.

## connect and disconnet

```zsh
warp-cli connect
```


