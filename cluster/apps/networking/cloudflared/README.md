# Cloudflare Tunnel

To create tunnel:

```
cloudflared tunnel login
cloudflared tunnel create k3s-homelab-0
cloudflared tunnel route dns k3s-homelab-0 tunnel.mydomainname.com
```

Route a service to the tunnel by adding annotations:
```
ingress:
    annotations:
        external-dns/is-public: "true"
        external-dns.alpha.kubernetes.io/cloudflare-proxied: "true"
        external-dns.alpha.kubernetes.io/target: "${SECRET_CLOUDFLARE_TUNNEL_ID}.cfargotunnel.com"
```
