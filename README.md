# wifiscan

这是用来扫描wifi的库，我修改了原作者的Linux部份，其实它是用了Linux的指令进行分析，而且分析都比较低极（/sbin/iw dev wlan0 scan -u）

```Go
package main

import (
    "context"
    "fmt"
    "github.com/soease/wifiscan"
)

func main() {
    ctx := context.Background()
    aps, _ := wifiscan.Scan(ctx, "wlp1s0")
    for _, ap := range aps {
        fmt.Printf("BSSID: %s  SSID: %-30s  Signal: %d\n", ap.BSSID, ap.SSID, ap.Signal)
    }
}

```

Supporting macOS and Linux. On Linux, this may need `sudo`.
