# tebbiworld NS8 repository

Software repository (module catalog) for the community modules by tebbiworld,
for [NethServer 8](https://github.com/NethServer/ns8-core).

Register it on a cluster (name `tebbiworld`):

```
api-cli run add-repository --data '{"name":"tebbiworld","url":"https://raw.githubusercontent.com/tebbiworld/ns8-repo/main/ns8/updates/","status":true,"testing":false}'
```

or in the cluster admin UI: Software Center → Repositories → Add repository.

| Module | Source | Image |
| --- | --- | --- |
| ARSnova | https://github.com/tebbiworld/ns8-arsnova | ghcr.io/tebbiworld/arsnova |
| ecoDMS | https://github.com/tebbiworld/ns8-ecodms | ghcr.io/tebbiworld/ecodms |
| Foundry VTT | https://github.com/tebbiworld/ns8-foundryvtt | ghcr.io/tebbiworld/foundryvtt |
| Hashtopolis | https://github.com/tebbiworld/ns8-hashtopolis | ghcr.io/tebbiworld/hashtopolis |
| Huginn | https://github.com/tebbiworld/ns8-huginn | ghcr.io/tebbiworld/huginn |
| netboot.xyz | https://github.com/tebbiworld/ns8-netbootxyz | ghcr.io/tebbiworld/netbootxyz |
| Open WebUI | https://github.com/tebbiworld/ns8-openwebui | ghcr.io/tebbiworld/openwebui |
| Plex Media Server | https://github.com/tebbiworld/ns8-plex | ghcr.io/tebbiworld/plex |
| SageMath | https://github.com/tebbiworld/ns8-sagemath | ghcr.io/tebbiworld/sagemath |
| TSA | https://github.com/tebbiworld/ns8-tsa | ghcr.io/tebbiworld/tsa |

## Maintenance

`ns8/updates/<module>/` holds `metadata.json` and `logo.png` per module; `repodata.json`
is generated with `createrepo.py` (inspects the published `:latest` image of every
module for its versions) and committed:

```
cd ns8/updates && /opt/repomd-venv/bin/python3 ../../createrepo.py . && cd ../.. && git add -A && git commit -m "<module> <version>" && git push
```

History note: until 2026-09-13 this catalog lived in the `repomd` branch of
`ns8-huginn`; that branch is kept for a while as a fallback and then removed.
