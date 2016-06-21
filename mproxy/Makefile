include $(TOPDIR)/rules.mk

PKG_NAME:=mproxy
PKG_VERSION:=0.3
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/boytm/mproxy.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=90c78442d343441db1547acd2909568682a175e6
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
# PKG_MIRROR_MD5SUM:=
# CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mproxy
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  DEPENDS:=+libevent2 +libopenssl +librt
  TITLE:= mproxy
endef

define Package/mproxy/description
  mproxy, a multi mode http proxy
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include
#TARGET_CFLAGS += -ggdb3

CMAKE_OPTIONS += -DENABLE_SS=1

define Package/mproxy/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mproxy $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/bin

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/mproxy.init $(1)/etc/init.d/mproxy
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/mproxy.conf $(1)/etc/
endef

$(eval $(call BuildPackage,mproxy))
