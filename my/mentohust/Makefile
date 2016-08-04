#
# Copyright (C) 2016 GuoGuo <gch981213@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mentohust
PKG_VERSION:=f855f50
PKG_RELEASE:=1
PKG_REV:=f855f50a70462ac4187e30d0d62e304331ef2058

PKG_SOURCE_PROTO:=git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/hyrathb/mentohust.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
include $(INCLUDE_DIR)/package.mk

define Package/mentohust
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libpcap
	TITLE:=An CERNET client daemon
	URL:=https://github.com/hyrathb/mentohust.git
	SUBMENU:=CERNET
endef

define Package/mentohust/description
An CERNET client daemon,
Most usually used in China collages.
endef

CONFIGURE_ARGS += \
	--disable-encodepass \
	--disable-notify \
	--disable-nls

# XXX: CFLAGS are already set by Build/Compile/Default
MAKE_FLAGS+= \
	OFLAGS=""

define Package/mentohust/conffiles
/etc/mentohust.conf
endef

define Package/mentohust/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mentohust $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/mentohust.conf $(1)/etc/
endef

$(eval $(call BuildPackage,mentohust))
