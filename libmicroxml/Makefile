include $(TOPDIR)/rules.mk

PKG_NAME:=libmicroxml
PKG_VERSION:=2018-06-14
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/pivasoftware/microxml.git
PKG_SOURCE_DATE:=2018-06-14
PKG_SOURCE_VERSION:=197ddb86711cfd2e8d7d777dc7c957e3472f6e1c
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=PIVA Software
PKG_LICENSE:=LGPL-2.1
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libmicroxml
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=microxml library for easycwmp
  URL:=https://github.com/pivasoftware/microxml
  DEPENDS:=+libpthread
endef

define Package/libmicroxml/description
  Minimal XML parser used by easycwmp TR-069 client.
endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/microxml.h $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libmicroxml.so* $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_BUILD_DIR)/microxml.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libmicroxml/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libmicroxml.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libmicroxml))
