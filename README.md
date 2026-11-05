# OpenWrt for the GL-MT3600BE

This repository is a fork of [OpenWrt](https://openwrt.org) with patches and configurations for the GL.iNet GL-MT3600BE (Beryl 7). They improve Ethernet, Wi-Fi and hardware offloading support, stability and performance on the router's MT7987 SoC and MT7990 Wi-Fi chip.

### Ethernet

- Full 2.5 Gbit/s between WAN and LAN, both directions at once
- Received packets spread over all CPU cores (RSS)
- Hardware flow offloading from the first packets, DSCP and ECN kept

### Wi-Fi

- Hardware offloading (WED 3.1), almost no CPU use
- Full-speed downloads that stay fast, with low latency for other traffic
- Stable roaming between radios and with 802.11r
- Sleeping devices stay connected
- Per-radio TX power, antennas and settings, shown correctly in LuCI
- DFS and firmware recovery that keep the 5 GHz radio running

### System

- Crash, memory leak and security fixes
- Status LED shows the internet connection
- CPU throttling at high temperature

...and many other fixes from MediaTek, Linux, hostapd and others.

## Patches

This repository adds 115 patches to OpenWrt. Each patch file keeps its author and source in its header.

<details>
<summary>From MediaTek feed (39)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [net: pcs: mtk-lynxi: correct power down setting](target/linux/mediatek/patches-6.18/742-net-pcs-mtk-lynxi-correct-power-down-setting.patch) | Bo-Cun Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/08196fa6e5d338ce88aa0002f781e2d24289b1f1/25.12/files/target/linux/mediatek/patches-6.12/999-pcs-05-mtk-lynxi-correct-power-down-setting.patch) |
| [net: ethernet: mtk_eth_soc: add XGMACv2 support for MT7987](target/linux/mediatek/patches-6.18/753-net-ethernet-mtk_eth_soc-add-XGMAC-v2-link-control.patch) | Bo-Cun Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-eth-14-mtk_eth_soc-add-XGMACv2-support-for-MT7987.patch) |
| [net: ethernet: mtk_eth_soc: revise mdc divider configuration for MT7987](target/linux/mediatek/patches-6.18/754-net-ethernet-mtk_eth_soc-fix-MT7987-MDC-divider.patch) | Bo-Cun Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-eth-37-mtk_eth_soc-revise-mdc-divider-configuration-for-MT7987.patch) |
| [net: ethernet: mtk_eth_soc: fix spurious MDIO timeout](target/linux/mediatek/patches-6.18/755-net-ethernet-mtk_eth_soc-fix-spurious-MDIO-timeout.patch) | Neal Yen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-eth-53-mtk_eth_soc-fix-spurious-mdio-timeout.patch) |
| [net: ethernet: mtk_eth_soc: fix memory leak on page pool creation failure](target/linux/mediatek/patches-6.18/756-net-ethernet-mtk_eth_soc-fix-page-pool-error-leak.patch) | Mason Chang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-eth-55-fix-memory-leak-on-page-pool-creation-failure.patch) |
| [net: ethernet: mtk_eth_soc: fix mtk_eth_offload_init memory leak](target/linux/mediatek/patches-6.18/758-net-ethernet-mtk_eth_soc-initialize-PPE-flow-table-once.patch) | Chak-Kei Lam | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-eth-43-mtk_eth_soc-fix-mtk_eth_offload_init-memory-leak.patch) |
| [net: phy: mediatek: serialize MT7987 firmware loading](target/linux/mediatek/patches-6.18/759-net-phy-mtk-2p5ge-serialize-MT7987-firmware-loading.patch) | MediaTek | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/718ecef786eff0dd507d678a8a9291ccbcf74aed) |
| [net: ethernet: mtk_eth_soc: use XMAC-v2 counters](target/linux/mediatek/patches-6.18/760-net-ethernet-mtk_eth_soc-use-XMAC-v2-counters.patch) | MediaTek, Paul-Louis Charrière | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/3a92b2d8eb5c14097b1d9ea12728837434aa5aa4) |
| [net: ethernet: mtk_ppe: fix typo for enabling MIB cache](target/linux/mediatek/patches-6.18/761-net-ethernet-mtk_ppe-fix-MIB-cache-enable.patch) | Bo-Cun Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-10-mtk_ppe-fix-typo-for-enabling-MIB-cache.patch) |
| [net: ethernet: mtk_eth_soc: use per-MAC SGMII syscfg0 mask](target/linux/mediatek/patches-6.18/762-net-ethernet-mtk_eth_soc-use-per-MAC-SGMII-syscfg0-mask.patch) | Evan Zhang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-eth-52-mtk_eth_soc-use-per-MAC-SGMII-syscfg0-mask.patch) |
| [net: ethernet: mtk_ppe: change TCP UDP aging out time](target/linux/mediatek/patches-6.18/766-net-ethernet-mtk_ppe-change-TCP-UDP-aging-out-time.patch) | Bo-Cun Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-12-mtk_ppe-change-TCP-UDP-aging-out-time.patch) |
| [net: ethernet: mtk_eth_soc: remove netsys v1 restriction for small frag check](target/linux/mediatek/patches-6.18/774-net-ethernet-mtk_eth_soc-remove-netsys-v1-restriction-for-small-frag-check.patch) | Mason Chang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/241d864218630c9cb380a3657c89f8fc3bdc3434/25.12/files/target/linux/mediatek/patches-6.12/999-eth-56-mtk_eth_soc-remove-netsys-v1-restriction-for-small-frag-check.patch) |
| [net: ethernet: mtk_wed: add MT7987 hardware path support](target/linux/mediatek/patches-6.18/947-net-ethernet-mtk_wed-add-MT7987-WED-3.1-support.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-wed-10-add-mt7987-hwpath-support.patch) |
| [net: ethernet: mtk_wed: add WDMA disable flow to WiFi L1 SER](target/linux/mediatek/patches-6.18/948-net-ethernet-mtk_wed-stabilize-reset-recovery.patch) | Bo-Cun Chen, Rex Lu, Paul-Louis Charrière | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-wed-13-net-ethernet-mtk_wed-add-WDMA-disable-flow-to-WiFi-L.patch) |
| [net: ethernet: mtk_wed: refactor IRQ get to avoid false status alerts](target/linux/mediatek/patches-6.18/949-net-ethernet-mtk_wed-avoid-v31-token-status-false-alarm.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/25.12/files/target/linux/mediatek/patches-6.12/999-wed-14-refactor-mtk_wed_irq_get-to-avoid-wed-status-false-a.patch) |
| [net: ethernet: mtk_wed: refactor WDMA init to avoid double initialization](target/linux/mediatek/patches-6.18/952-net-ethernet-mtk_wed-refactor-WDMA-init-to-avoid-double-init.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-wed-16-refactor-wdma-init-flow-to-avoid-double-init.patch) |
| [refactor check wed module busy time](target/linux/mediatek/patches-6.18/953-net-ethernet-mtk_wed-shorten-busy-poll.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-wed-20-refactor-check-wed-module-busy-time.patch) |
| [net: ethernet: mtk_eth_soc: add PSE port link handling for MAC ports](target/linux/mediatek/patches-6.18/956-net-ethernet-mtk_eth_soc-handle-PSE-port-link-state.patch) | Bo-Cun Chen, Paul-Louis Charrière | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-eth-48-mtk_eth_soc-add-PSE-port-link-handling-for-MAC-ports.patch) |
| [net: ethernet: mtk_wed: debugfs: fix the HIFTXD MSDU counter offsets](target/linux/mediatek/patches-6.18/962-net-ethernet-mtk_wed-debugfs-fix-the-HIFTXD-MSDU-counter-offsets.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/08196fa6e5d338ce88aa0002f781e2d24289b1f1/25.12/files/target/linux/mediatek/patches-6.12/999-wed-08-extended-wed-debugfs.patch) |
| [net: ethernet: mtk_wed: size the TX buffer pool from the token count](target/linux/mediatek/patches-6.18/963-net-ethernet-mtk_wed-size-the-TX-buffer-pool-from-the-token-count.patch) | Rex Lu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/0a986b74baf1461993b2eccfd9be371c7d887afc/25.12/files/target/linux/mediatek/patches-6.12/999-wed-23-Add-adjust-TX_BM_PKT_CNT-based-on-hw-token.patch) |
| [net: ethernet: mtk_ppe: add PPE cache preserved line lock](target/linux/mediatek/patches-6.18/986-net-ethernet-mtk_ppe-add-PPE-cache-preserved-line-lock.patch) | Bo-Cun Chen, Paul-Louis Charrière | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/08196fa6e5d338ce88aa0002f781e2d24289b1f1/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-14-mtk_ppe-add-PPE-cache-preserved-line-lock.patch) |
| [mtk: mt76: mt7996: Fix spinlock usage to prevent AP panic](package/kernel/mt76/patches/100-mt7996-fix-register-remap-locking.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/4e825214deaafc5cdc5457d66a1a828449f07e69) |
| [mtk: mt76: mt7996: check if link BSS is initialized before dofing vif_link_remove](package/kernel/mt76/patches/101-mt7996-skip-uninitialized-vif-link-removal.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/c6b206f391358af2fee96389544162838505fd1f) |
| [mtk: mt76: mt7990: add mt7987 wed hw path support](package/kernel/mt76/patches/102-mt7996-add-MT7987-WED-3.1-data-path.patch) | Rex Lu, Paul-Louis Charrière | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0049-mtk-mt76-mt7990-add-mt7987-wed-hw-path-support.patch) |
| [wifi: mt76: mt7996: use dedicated MT7990 TX-free ring for WED](package/kernel/mt76/patches/104-mt7996-use-dedicated-MT7990-TX-free-ring-for-WED.patch) | Peter Chiu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0048-mtk-mt76-mt7996-add-configuration-to-suppot-wed-and-.patch) |
| [wifi: mt76: mt7996: initialize MT7990 band-1 RRO ring](package/kernel/mt76/patches/106-mt7996-initialize-MT7990-band-1-RRO-ring.patch) | Peter Chiu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0048-mtk-mt76-mt7996-add-configuration-to-suppot-wed-and-.patch) |
| [mtk: mt76: add mask for Q_READ and Q_WRITE](package/kernel/mt76/patches/108-mt76-preserve-packed-DMA-ring-control-fields.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0046-mtk-mt76-add-mask-for-Q_READ-and-Q_WRITE.patch) |
| [wifi: mt76: mt7996: separate WED and software token ranges](package/kernel/mt76/patches/109-mt7996-separate-WED-and-software-token-ranges.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0054-mtk-mt76-add-debug-tools.patch) |
| [mtk: mt76: mt7996: clear ieee80211_tx_info->status before use](package/kernel/mt76/patches/110-mt76-clear-stale-TX-status-before-completion.patch) | Michael-CY Lee | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/4b573a7e757e53e638521be26d686084df058bf2) |
| [mtk: mt76: mt7996: Support MCU message retry by separating prepare and send](package/kernel/mt76/patches/127-mt7996-retry-MCU-messages.patch) | Peter Chiu | [Link](https://github.com/mediatek/mtk-openwrt-feeds/commit/77fa6f88a72b8d442e44fca881f90adca38199f1) |
| [wifi: mt76: mt7996: enable firmware RED with WED 3.1](package/kernel/mt76/patches/130-mt7996-enable-firmware-RED-with-WED-3.1.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/08196fa6e5d338ce88aa0002f781e2d24289b1f1/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0054-mtk-mt76-add-debug-tools.patch) |
| [mtk: mt76: fix the behavior of radar detection for bootup CAC](package/kernel/mt76/patches/132-mt7996-resume-TX-after-a-radar-during-the-start-up-CAC.patch) | StanleyYP Wang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/4c3096b7487cf54c9396c1e1b8c5841e24bfaf85/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0127-cp-mtk-mt76-fix-the-behavior-of-radar-detection-for-boo.patch) |
| [mt7996: read the byte counters of both ADM_STAT event versions](package/kernel/mt76/patches/133-mt7996-read-the-byte-counters-of-both-ADM_STAT-event-versions.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/7a38cb57511c6884638d72e26aaa14eb34c496c6/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0044-mtk-mt76-rework-statistics-report-for-mt7996.patch) |
| [mtk: mac80211: relax the DFS restrictions for scanning](package/kernel/mac80211/patches/subsys/903-mtk-mac80211-relax-the-DFS-restrictions-for-scanning.patch) | StanleyYP Wang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/a15454c888f4f4144c50e33b5feef4f247c5f78b/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mac80211/patches/subsys/0108-mtk-mac80211-relax-the-DFS-restrictions-for-scanning.patch) |
| [mtk: cfg80211: fix crash in cfg80211_sta_set_mld_sinfo()](package/kernel/mac80211/patches/subsys/904-cfg80211-guard-missing-per-tid-link-stats.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mac80211/patches/subsys/0109-mtk-cfg80211-fix-crash-in-cfg80211_sta_set_mld_sinfo.patch) |
| [mtk: mac80211: fix radio idx missing after replace ctx](package/kernel/mac80211/patches/subsys/905-mtk-mac80211-fix-radio-idx-missing-after-replace-ctx.patch) | StanleyYP Wang | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mac80211/patches/subsys/0093-mtk-mac80211-fix-radio-idx-missing-after-replace-ctx.patch) |
| [mtk: hostapd: clear authroized flag when removing STA from the driver during association handling](package/network/services/hostapd/patches/901-AP-clear-the-authorized-flag-when-removing-the-STA-from-the-driver-during-association.patch) | Michael-CY Lee | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/08196fa6e5d338ce88aa0002f781e2d24289b1f1/autobuild/unified/filogic/mac80211/25.12/files/package/network/services/hostapd/patches/0111-mtk-hostapd-clear-authroized-flag-when-removing-STA-.patch) |
| [mtk: iw: support per-radio txpower setting](package/network/utils/iw/patches/320-mtk-iw-support-per-radio-txpower-setting.patch) | Shayne Chen | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/network/utils/iw/patches/0009-mtk-iw-support-per-radio-txpower-setting.patch) |
| [mtk: iw: allow to specify radio_idx when setting TX/RX antenna](package/network/utils/iw/patches/321-mtk-iw-allow-to-specify-radio_idx-when-setting-TX-RX-antenna.patch) | Michael-CY Lee | [Link](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/network/utils/iw/patches/0010-mtk-iw-allow-to-specify-radio_idx-when-setting-TX-RX.patch) |

</details>

<details>
<summary>From PRs (5)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [netfilter: flowtable: fetch hardware counters before removing a flow](target/linux/generic/pending-6.18/708-netfilter-flowtable-fetch-hardware-counters-before-r.patch) | Valentin Berezhnoy | [openwrt/openwrt#26107](https://github.com/openwrt/openwrt/pull/26107) |
| [net: ethernet: mediatek: preserve PPE flow accounting](target/linux/generic/pending-6.18/736-06-net-ethernet-mediatek-preserve-sibling-ppe-bindings.patch) | Alexander Goodkind | [openwrt/openwrt#26107](https://github.com/openwrt/openwrt/pull/26107) |
| [wifi: mt76: mt7996: advertise VHT beamformee STS 2 on MT7990](package/kernel/mt76/patches/136-mt7996-advertise-VHT-beamformee-STS-2-on-MT7990.patch) | Eugene Bykov | [openwrt/mt76#1153](https://github.com/openwrt/mt76/pull/1153) |
| [wifi: mt76: mt7996: handle station airtime counter resets](package/kernel/mt76/patches/900-mt7996-handle-station-airtime-counter-resets.patch) | David Mestre | [openwrt/openwrt#26037](https://github.com/openwrt/openwrt/pull/26037) |
| [nl80211: clear nl80211 freqlist entry](package/network/utils/iwinfo/patches/130-nl80211-clear-nl80211-freqlist-entry.patch) | Ruslan Isaev | [openwrt/iwinfo#42](https://github.com/openwrt/iwinfo/pull/42) |

</details>

<details>
<summary>From Linux (14)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [net: phylink: initialise link_state before a forced major config](target/linux/generic/backport-6.18/707-v7.3-net-phylink-initialise-link_state-before-a-forced-major-config.patch) | Aleksei Sviridkin | [Link](https://github.com/torvalds/linux/commit/113998aa372f4869bf62cfc75c28a2849e8487be) |
| [wifi: mt76: fix queue assignment for disassoc packets](package/kernel/mt76/patches/113-mt76-route-disassoc-frames-to-ALTXQ.patch) | Peter Chiu | [Link](https://github.com/torvalds/linux/commit/3999d15cfcc72a946ec419c4059b0e0cd7860053) |
| [wifi: cfg80211: fix RTS threshold setting for single-radio PHY](package/kernel/mac80211/patches/subsys/900-wifi-cfg80211-fix-RTS-threshold-setting-for-single-r.patch) | Stanislaw Gruszka | [Link](https://github.com/torvalds/linux/commit/9eda41e32263806a66835e275efdcc0c5f46bbc4) |
| [wifi: mac80211: send TWT teardown to peer after setup TX failure](package/kernel/mac80211/patches/subsys/909-wifi-mac80211-send-TWT-teardown-to-peer-after-setup.patch) | Zhao Li | [Link](https://github.com/torvalds/linux/commit/a28fcce6ee74be8a4526e6cfa16dc7786d62a784) |
| [wifi: cfg80211: check IP header size in cfg80211_classify8021d()](package/kernel/mac80211/patches/subsys/910-wifi-cfg80211-check-IP-header-size-in-cfg80211_class.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/48b2c5c628b09cf36cbeca53e0432fc2a7518be7) |
| [wifi: cfg80211: don't free driver-owned scan requests](package/kernel/mac80211/patches/subsys/911-wifi-cfg80211-don-t-free-driver-owned-scan-requests.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/dab68a74e90b8e07f08ed9deaa5884857a3cfe89) |
| [wifi: cfg80211: only group hidden BSSes with beacon entries](package/kernel/mac80211/patches/subsys/912-wifi-cfg80211-only-group-hidden-BSSes-with-beacon-en.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/068843ed0902c552a13860c5ec6b2ca65b57a065) |
| [wifi: mac80211: reset state when starting AP fails](package/kernel/mac80211/patches/subsys/913-wifi-mac80211-reset-state-when-starting-AP-fails.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/3f28551d0241254a75626d868041c6340285088b) |
| [wifi: mac80211: reset the AP_VLAN tailroom counter on ifdown](package/kernel/mac80211/patches/subsys/914-wifi-mac80211-reset-the-AP_VLAN-tailroom-counter-on.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/4504f3960dc4501c73be9f99eabda2e26e9db41e) |
| [wifi: mac80211: set up the TX info early to fix failure paths](package/kernel/mac80211/patches/subsys/915-wifi-mac80211-set-up-the-TX-info-early-to-fix-failur.patch) | Johannes Berg | [Link](https://github.com/torvalds/linux/commit/50d3d79dc0743b616afb00d01a626c76758721f7) |
| [wifi: mac80211: drop oversized fragments to avoid extra_len overflow](package/kernel/mac80211/patches/subsys/916-wifi-mac80211-drop-oversized-fragments-to-avoid-extr.patch) | Yuchao Zhang | [Link](https://github.com/torvalds/linux/commit/5e4f3509793b4db2c0835340224743db680e861f) |
| [wifi: mac80211: prevent AP VLAN tx from other interfaces](package/kernel/mac80211/patches/subsys/917-wifi-mac80211-prevent-AP-VLAN-tx-from-other-interfac.patch) | Felix Fietkau | [Link](https://github.com/torvalds/linux/commit/7f93ca31f7fd9b42e7d692f59514436d448ac908) |
| [wifi: mac80211: count only matching reservations in reserved switch](package/kernel/mac80211/patches/subsys/918-wifi-mac80211-count-only-matching-reservations-in-re.patch) | Zhiling Zou | [Link](https://github.com/torvalds/linux/commit/437f3727b4fd715266c296435c116288f82666fd) |
| [wifi: mac80211: keep paired old chanctx alive](package/kernel/mac80211/patches/subsys/919-wifi-mac80211-keep-paired-old-chanctx-alive.patch) | Zhiling Zou | [Link](https://github.com/torvalds/linux/commit/3412e9a800786d1dec4a58367db1cba275e7ef11) |

</details>

<details>
<summary>From Linux mailing lists (3)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [netfilter: flowtable: flush delete work after final GC](target/linux/mediatek/patches-6.18/769-netfilter-flowtable-flush-delete-work-after-final-GC.patch) | Chengfeng Ye | [Link](https://patchwork.ozlabs.org/project/netfilter-devel/patch/20260927163248.1002656-1-nicoyip.dev@gmail.com/) |
| [net: ethernet: mtk_eth_soc: Add register definitions for RSS and LRO](target/linux/mediatek/patches-6.18/980-net-ethernet-mtk_eth_soc-add-register-definitions-for-RSS-and-LRO.patch) | Mason Chang | [Link](https://patchwork.kernel.org/project/netdevbpf/patch/20260509190938.169290-2-linux@fw-web.de/) |
| [net: ethernet: mtk_eth_soc: Add RSS support](target/linux/mediatek/patches-6.18/981-net-ethernet-mtk_eth_soc-add-RSS-support.patch) | Mason Chang, Paul-Louis Charrière | [Link](https://patchwork.kernel.org/project/netdevbpf/patch/20260509190938.169290-3-linux@fw-web.de/) |

</details>

<details>
<summary>From mt76 (1)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [wifi: mt76: mt7996: use the default timeout for STA_REC and BSS_INFO updates](package/kernel/mt76/patches/126-mt7996-use-the-default-timeout-for-STA_REC-and-BSS_INFO-updates.patch) | Felix Fietkau | [Link](https://github.com/openwrt/mt76/commit/00107991a25e6212156d27ce9075448057e12a7f) |

</details>

<details>
<summary>From hostapd (5)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [FT: Fix off-by-2 buffer bounds check in wpa_ft_process_rdie()](package/network/services/hostapd/patches/902-FT-Fix-off-by-2-buffer-bounds-check-in-wpa_ft_proces.patch) | Brandon Arrendondo | [Link](https://w1.fi/cgit/hostap/commit/?id=fcae90b60f0ef098c216f2fb528b63b77360febe) |
| [EHT: Fix OOB read in hostapd_parse_link_reconf_req_sta_profile()](package/network/services/hostapd/patches/903-EHT-Fix-OOB-read-in-hostapd_parse_link_reconf_req_st.patch) | Brandon Arrendondo | [Link](https://w1.fi/cgit/hostap/commit/?id=652a34915762e4edbdba2ee70e18545e749ef132) |
| [AP: Fix OOB read of STA's HE-MCS map in check_valid_he_mcs()](package/network/services/hostapd/patches/904-AP-Fix-OOB-read-of-STA-s-HE-MCS-map-in-check_valid_h.patch) | Brandon Arrendondo | [Link](https://w1.fi/cgit/hostap/commit/?id=6cf41afd5bb7ce187f415146750a60d18d90f1c9) |
| [SAE: Make sure the needed state is available in sae_write_confirm()](package/network/services/hostapd/patches/905-SAE-Make-sure-the-needed-state-is-available-in-sae_w.patch) | Jouni Malinen | [Link](https://w1.fi/cgit/hostap/commit/?id=0605d9ddc15a421b6ef57e0ff9e353fd0b76e898) |
| [nl80211: Update AP MLD active_links bitmap during start_ap](package/network/services/hostapd/patches/906-nl80211-Update-AP-MLD-active_links-bitmap-during-sta.patch) | Manish Dharanenthiran | [Link](https://w1.fi/cgit/hostap/commit/?id=4a9a301a2d6528ce1085f1b170101b08b86076b6) |

</details>

<details>
<summary>Written for this repository (48)</summary>

| Patch | Author | Source |
| --- | --- | --- |
| [net: ethernet: mtk_eth_soc: release PPE tables on remove](target/linux/mediatek/patches-6.18/763-net-ethernet-mtk_eth_soc-release-PPE-tables-on-remove.patch) | Paul-Louis Charrière, based on work by Chak-Kei Lam | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-33-net-ethernet-mtk_eth_soc-fix-mtk_eth_offload_init-memory-leak.patch) |
| [net: ethernet: mtk_ppe: remove debugfs on deinit](target/linux/mediatek/patches-6.18/764-net-ethernet-mtk_ppe-remove-debugfs-on-deinit.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_eth_soc: order driver removal safely](target/linux/mediatek/patches-6.18/765-net-ethernet-mtk_eth_soc-order-driver-removal.patch) | Paul-Louis Charrière |  |
| [netfilter: nf_flow_table: tear down flows on bridge FDB moves](target/linux/mediatek/patches-6.18/767-netfilter-nf_flow_table-tear-down-flows-on-bridge-FDB-moves.patch) | Paul-Louis Charrière, based on work by Bo-Cun Chen and Chad Monroe | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-08-mtk_ppe-add-roaming-handler.patch), [Chad Monroe's tree](https://github.com/cmonroe/target-mediatek/blob/c18b780f63a277dfc574d0ee61b5e60c94642ea7/cascade/patches-6.18/990-01-smartrg-netfilter-nf_flow_table-invalidate-flows-on-bridge-FDB-roaming.patch) |
| [netfilter: nf_flow_table: remove hardware flows before unbinding](target/linux/mediatek/patches-6.18/768-netfilter-nf_flow_table-remove-hardware-flows-before-unbinding.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_ppe: bind flows from their first packets](target/linux/mediatek/patches-6.18/770-net-ethernet-mtk_ppe-bind-flows-from-their-first-packets.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_eth_soc: fix netdev notifier lifetime](target/linux/mediatek/patches-6.18/772-net-ethernet-mtk_eth_soc-fix-netdev-notifier-lifetime.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_eth_soc: update SYSCFG0 bits atomically](target/linux/mediatek/patches-6.18/773-net-ethernet-mtk_eth_soc-update-SYSCFG0-bits-atomically.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_wed: fix A-MSDU buffer leaks](target/linux/mediatek/patches-6.18/954-net-ethernet-mtk_wed-fix-A-MSDU-buffer-leaks.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_eth_soc: add MT7987 misc error IRQ](target/linux/mediatek/patches-6.18/957-net-ethernet-mtk_eth_soc-add-MT7987-misc-error-IRQ.patch) | Paul-Louis Charrière, based on work by MediaTek | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/commit/13c73de25ef3f53f5dabdc2f2b410f3aaccbcd0d) |
| [net: ethernet: mtk_wed: flush PPE entries of removed stations](target/linux/mediatek/patches-6.18/958-net-ethernet-mtk_wed-flush-PPE-entries-of-removed-stations.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_ppe: show WDMA target in debugfs](target/linux/mediatek/patches-6.18/959-net-ethernet-mtk_ppe-show-WDMA-target-in-debugfs.patch) | Paul-Louis Charrière |  |
| [net: ethernet: mtk_eth_soc: enable RSS on MT7987](target/linux/mediatek/patches-6.18/982-net-ethernet-mtk_eth_soc-enable-RSS-on-MT7987.patch) | Paul-Louis Charrière, based on work by Mason Chang | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/25.12/files/target/linux/mediatek/patches-6.12/999-eth-09-mtk_eth_soc-add-rss-support.patch) |
| [net: ethernet: mtk_eth_soc: read XMAC-v2 counters before they wrap](target/linux/mediatek/patches-6.18/983-net-ethernet-mtk_eth_soc-read-XMAC-v2-counters-before-they-wrap.patch) | Paul-Louis Charrière, based on work by Bo-Cun Chen | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/25.12/files/target/linux/mediatek/patches-6.12/999-eth-11-mtk_eth_soc-refactor-forced-reset-monitor.patch) |
| [net: ethernet: mtk_ppe: bypass QDMA between ports without a switch](target/linux/mediatek/patches-6.18/984-net-ethernet-mtk_ppe-bypass-QDMA-between-ports-without-a-switch.patch) | Paul-Louis Charrière, based on work by Bo-Cun Chen | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-04-mtk_ppe-change-to-internal-QoS-mode.patch) |
| [net: ethernet: mtk_ppe: keep DSCP and ECN of offloaded flows](target/linux/mediatek/patches-6.18/985-net-ethernet-mtk_ppe-keep-DSCP-and-ECN-of-offloaded-flows.patch) | Paul-Louis Charrière, based on work by Bo-Cun Chen | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/25.12/files/target/linux/mediatek/patches-6.12/999-ppe-23-mtk_ppe-add-keep-dscp-toggle.patch) |
| [net: ethernet: mtk_wed: unbind the WLAN driver before the Ethernet driver](target/linux/mediatek/patches-6.18/987-net-ethernet-mtk_wed-unbind-the-WLAN-driver-before-the-Ethernet-driver.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: skip secondary WED without primary](package/kernel/mt76/patches/103-mt7996-skip-secondary-WED-without-primary.patch) | Paul-Louis Charrière, based on work by Rex Lu | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0040-mtk-mt76-mt7996-Fix-call-trace-happened-when-wed-att.patch) |
| [wifi: mt76: mt7996: route MT7990 TX-free notifications from MAC](package/kernel/mt76/patches/105-mt7996-route-MT7990-TX-free-notifications-from-MAC.patch) | Paul-Louis Charrière | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/671c2416d6219beb19abbb05709e418a6363be62/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0054-mtk-mt76-add-debug-tools.patch) |
| [wifi: mt76: mt7996: take MT7990 TX rate from firmware report](package/kernel/mt76/patches/107-mt7996-take-MT7990-TX-rate-from-firmware-report.patch) | Paul-Louis Charrière, based on work by Benjamin Lin and Shayne Chen | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/autobuild/unified/filogic/mac80211/24.10/files/package/kernel/mt76/patches/0017-mtk-mt76-mt7996-update-TX-RX-rates-via-MCU-command.patch) |
| [wifi: mt76: delete only the RX NAPIs that were added](package/kernel/mt76/patches/111-mt76-delete-only-the-RX-NAPIs-that-were-added.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: free DMA descriptor rings on cleanup](package/kernel/mt76/patches/112-mt76-free-DMA-descriptor-rings-on-cleanup.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: flush WED PPE entries on station removal](package/kernel/mt76/patches/115-mt7996-flush-WED-PPE-entries-on-station-removal.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: restart the radar detector after a full reset](package/kernel/mt76/patches/117-mt7996-restart-the-radar-detector-after-a-full-reset.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: keep the TX PN across a full reset](package/kernel/mt76/patches/118-mt7996-keep-the-TX-PN-across-a-full-reset.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: send no beacon for a link the firmware does not know](package/kernel/mt76/patches/119-mt7996-send-no-beacon-for-a-link-the-firmware-does-not-know.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: start the MAC work of running radios only after a reset](package/kernel/mt76/patches/120-mt7996-start-the-MAC-work-of-running-radios-only-after-a-reset.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: support per-radio RTS threshold, coverage class and antennas](package/kernel/mt76/patches/121-mt7996-support-per-radio-RTS-threshold-coverage-class-and-antennas.patch) | Paul-Louis Charrière, based on work by Michael-CY Lee | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mt76/patches/0076-mtk-mt76-mt7996-allow-setting-antenna-with-radio_idx.patch) |
| [wifi: mt76: mt7996: apply the RTS threshold and coverage class when a radio starts](package/kernel/mt76/patches/122-mt7996-apply-the-RTS-threshold-and-coverage-class-when-a-radio-starts.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: keep the default RTS threshold after a hardware restart](package/kernel/mt76/patches/123-mt7996-keep-the-default-RTS-threshold-after-a-hardware-restart.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: keep power save buffering for nullfunc probes](package/kernel/mt76/patches/124-mt76-keep-power-save-buffering-for-nullfunc-probes.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: reset after an MCU timeout only once the device is registered](package/kernel/mt76/patches/128-mt7996-reset-after-an-MCU-timeout-only-once-the-device-is-registered.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: report radar on the channel context of its radio](package/kernel/mt76/patches/129-mt7996-report-radar-on-the-channel-context-of-its-radio.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: use 4096 WED TX tokens with WED 3.1](package/kernel/mt76/patches/131-mt7996-use-4096-WED-TX-tokens-with-WED-3.1.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: drop 802.3 frames that fail the PN check](package/kernel/mt76/patches/134-mt76-drop-802.3-frames-that-fail-the-PN-check.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: release a pending A-MSDU when a WED RX queue is empty](package/kernel/mt76/patches/135-mt76-release-a-pending-A-MSDU-when-a-WED-RX-queue-is-empty.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: take MT7990 RX rate from firmware report](package/kernel/mt76/patches/137-mt7996-take-MT7990-RX-rate-from-firmware-report.patch) | Paul-Louis Charrière, based on work by Benjamin Lin | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/f7eec2ff2e4fc8ded3439d7805c0aaa030ef9e07/autobuild/unified/filogic/mac80211/24.10/files/package/kernel/mt76/patches/0017-mtk-mt76-mt7996-update-TX-RX-rates-via-MCU-command.patch) |
| [wifi: mt76: mt7996: upload the keys of a reused link](package/kernel/mt76/patches/138-mt7996-upload-the-keys-of-a-reused-link.patch) | Paul-Louis Charrière |  |
| [wifi: mt76: mt7996: keep a WCID on its band](package/kernel/mt76/patches/139-mt7996-keep-a-wcid-on-its-band.patch) | Paul-Louis Charrière |  |
| [wifi: cfg80211/mac80211: support per-radio TX power](package/kernel/mac80211/patches/subsys/906-wifi-cfg80211-mac80211-support-per-radio-TX-power.patch) | Paul-Louis Charrière, based on work by Shayne Chen | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mac80211/patches/subsys/0113-mtk-nl80211-support-per-radio-txpower-setting.patch) |
| [wifi: cfg80211/mac80211: support per-radio antennas and coverage class](package/kernel/mac80211/patches/subsys/907-wifi-cfg80211-mac80211-support-per-radio-antennas-and-coverage-class.patch) | Paul-Louis Charrière, based on work by Michael-CY Lee | [MediaTek feed](https://github.com/mediatek/mtk-openwrt-feeds/blob/22213a321b6dafb2a5e01def97363420e6e938fd/autobuild/unified/filogic/mac80211/25.12/files/package/kernel/mac80211/patches/subsys/0123-mtk-mac80211-allow-setting-antenna-with-radio_idx.patch) |
| [wifi: mac80211: resend the restart delBA once the station is heard](package/kernel/mac80211/patches/subsys/926-wifi-mac80211-resend-the-restart-delBA-once-the-stat.patch) | Paul-Louis Charrière |  |
| [wifi: cfg80211: keep a DFS channel available until START_AP](package/kernel/mac80211/patches/subsys/927-wifi-cfg80211-keep-a-DFS-channel-available-until-START_AP.patch) | Paul-Louis Charrière |  |
| [nl80211: Report probe client events to the correct BSS](package/network/services/hostapd/patches/900-nl80211-report-probe-client-events-to-the-correct-BSS.patch) | Paul-Louis Charrière |  |
| [DFS: Run a CAC when the kernel refuses a channel whose CAC was skipped](package/network/services/hostapd/patches/907-DFS-run-a-CAC-when-the-kernel-refuses-a-channel-whose-CAC-was-skipped.patch) | Paul-Louis Charrière |  |
| [iw: allow setting the coverage class of a radio](package/network/utils/iw/patches/322-iw-allow-setting-the-coverage-class-of-a-radio.patch) | Paul-Louis Charrière |  |
| [nl80211: resolve interfaces on multi-radio wiphys](package/network/utils/iwinfo/patches/110-nl80211-resolve-multi-radio-interfaces.patch) | Paul-Louis Charrière |  |
| [nl80211: limit multi-radio modes to the selected band](package/network/utils/iwinfo/patches/120-nl80211-limit-modes-to-multi-radio-band.patch) | Paul-Louis Charrière |  |

</details>

## Configuration

These defaults differ from OpenWrt on this router:

- Wi-Fi hardware offloading (WED 3.1) is enabled.
- Hardware flow offloading is enabled on first boot, unless the firewall already sets flow offloading or an SQM queue is enabled.
- The 5 GHz radio uses a 4 ms TX burst, unless `tx_queue_data2_burst` is already set.
- The firewall rule `DNS-answers-VI`, added on first boot, marks the router's DNS answers CS5, so a download to the same Wi-Fi client does not delay or drop them.
- The status LED shows the WAN state: white while online, blinking blue while offline, blue during boot, failsafe and upgrade.
- The MT7987 2.5G PHY uses firmware v7.3 from MediaTek's feed, downloaded at a fixed commit and checked by hash.
- `libiwinfo` is part of the image, so installing LuCI later keeps the patched library.
- CPU frequency cooling is enabled, so the 117 °C trip point throttles the CPUs.

## Download

Download the sysupgrade image from the [latest release](https://github.com/plcharriere/gl-mt3600be-openwrt/releases/latest).

Copy it to the router and flash it:

```sh
scp -O openwrt-mediatek-filogic-glinet_gl-mt3600be-squashfs-sysupgrade.bin root@192.168.1.1:/tmp/
ssh root@192.168.1.1 sysupgrade -n /tmp/openwrt-mediatek-filogic-glinet_gl-mt3600be-squashfs-sysupgrade.bin
```

The `-n` option starts from a clean configuration.

### From the stock firmware

Open http://192.168.8.1, go to System > Upgrade > Local Upgrade, upload the image and turn off Keep Settings. The router comes back at 192.168.1.1.

## Build

Use a Linux build host with the standard OpenWrt build prerequisites installed:

```sh
git clone --single-branch https://github.com/plcharriere/gl-mt3600be-openwrt.git
cd gl-mt3600be-openwrt

./scripts/feeds update -a
./scripts/feeds install -a

printf '%s\n' \
  'CONFIG_TARGET_mediatek=y' \
  'CONFIG_TARGET_mediatek_filogic=y' \
  'CONFIG_TARGET_mediatek_filogic_DEVICE_glinet_gl-mt3600be=y' \
  > .config

make defconfig
make -j"$(nproc)" V=s
```

The sysupgrade image is produced at:

```text
bin/targets/mediatek/filogic/openwrt-mediatek-filogic-glinet_gl-mt3600be-squashfs-sysupgrade.bin
```

## Contributing

[Issues](https://github.com/plcharriere/gl-mt3600be-openwrt/issues) and [pull requests](https://github.com/plcharriere/gl-mt3600be-openwrt/pulls) are welcome, and so are test results and measurements from your own setup.

## License

OpenWrt is licensed under GPL-2.0.
