include $(TOPDIR)/rules.mk

PKG_NAME:=netkeeper
PKG_RELEASE:=2
PKG_VERSION:=76ba26b

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk


define Package/netkeeper
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Netkeeper
	DEPENDS:=+ppp-mod-pppoe
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Package/netkeeper/install
	$(INSTALL_DIR) $(1)/usr/lib/pppd/2.4.7
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/builds/*.so $(1)/usr/lib/pppd/2.4.7
	$(INSTALL_DIR) $(1)/lib/netifd/proto
	$(INSTALL_BIN) ./files/netkeeper.sh $(1)/lib/netifd/proto/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
