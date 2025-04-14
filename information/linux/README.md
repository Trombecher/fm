# Font Management On Linux

## Location

* System-wide font location: `/usr/share/fonts`
* Per-user fonts `/home/<USER>/.local/share/fonts`

## Reload Font Cache

```bash
sudo fc-cache -f -v
```

## Sources

* FontConfig: https://github.com/behdad/fontconfig/tree/master