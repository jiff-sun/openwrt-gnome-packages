include $(TOPDIR)/rules.mk

PKG_NAME:=libsoup
PKG_VERSION:=2.26.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.26
PKG_MD5SUM:=

PKG_FIXUP:=libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libsoup
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libsoup
  URL:=http://live.gnome.org/LibSoup
  DEPENDS:=+glib2 +libxml2 +libgnutls
endef

define Build/Configure
	$(call Build/Configure/Default, \
        --enable-ssl \
        --disable-glibtest \
        --without-apache-httpd \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libsoup-2.4/libsoup}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libsoup-2.4.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libsoup-2.4/libsoup/*.h \
		$(1)/usr/include/libsoup-2.4/libsoup/
endef

define Package/libsoup/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libsoup-2.4.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsoup))
