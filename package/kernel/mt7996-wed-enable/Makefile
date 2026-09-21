include $(TOPDIR)/rules.mk

PKG_NAME:=mt7996-wed-enable
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define Package/mt7996-wed-enable
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=Enable MediaTek MT7996-family WED offload
  DEPENDS:=@TARGET_mediatek_filogic +kmod-mt7996e
endef

define Package/mt7996-wed-enable/description
 Enable the mt7996e WED data path at module load time. This package is
 intended for device profiles whose WED hardware is supported by both the
 Ethernet and Wi-Fi drivers.
endef

define Build/Compile
endef

define Package/mt7996-wed-enable/install
	$(INSTALL_DIR) $(1)/etc/modules.d
	$(INSTALL_DATA) ./files/99-mt7996e-wed $(1)/etc/modules.d/99-mt7996e-wed
endef

$(eval $(call BuildPackage,mt7996-wed-enable))
