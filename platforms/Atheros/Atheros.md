Atheros-based wireless products
====

# Common problems

## TX-power issues
AR9XXX stuff seems to refuse to increase tx-power under some situations ([here](https://dev.archive.openwrt.org/ticket/11896) is a well documented example) - apparently mostly when running hostapd.

### Resources
https://openwrt.org/docs/guide-user/network/wifi/transmit.power.limits

### Tasks
- [ ] Try out using `scan` to force set
- [ ] Try out hard-coding higher values into the` hostapd.conf`
