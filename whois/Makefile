#
# Copyright (C) 2011-2018 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=whois
PKG_VERSION:=5.4.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://ftp.debian.org/debian/pool/main/w/whois
PKG_HASH:=3775ae0cfaa6dd8d886e5233c4826225cddcb88c99c2a08130d14e15fe58e378

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
# libidn2.so: undefined reference to `libintl_gettext'
include $(INCLUDE_DIR)/nls.mk

define Package/whois
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libidn2
	TITLE:=intelligent WHOIS client
	URL:=http://ftp.debian.org/debian/pool/main/w/whois
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/whois/description
 This package provides a commandline client for the WHOIS (RFC 3912) protocol,
 which queries online servers for information such as contact details
 for domains and IP address assignments. It can intelligently select
 the appropriate WHOIS server for most queries.
endef

define Package/whois/conffiles
/opt/etc/whois.conf
endef

define Package/whois/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/whois $(1)/opt/sbin
	$(INSTALL_DIR) $(1)/opt/etc
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/whois.conf $(1)/opt/etc/whois.conf
endef

$(eval $(call BuildPackage,whois))
