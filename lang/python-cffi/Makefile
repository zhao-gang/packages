#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=cffi
PKG_VERSION:=1.5.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/c/cffi
PKG_MD5SUM:=dec8441e67880494ee881305059af656

PKG_BUILD_DEPENDS:=python python-setuptools
HOST_BUILD_DEPENDS:=libffi/host python/host python-setuptools/host python-pycparser/host

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python-host.mk)

define Package/python-cffi
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-cffi
	URL:=http://cffi.readthedocs.org/
	DEPENDS:=+libffi +python-light +python-pycparser @BROKEN
endef

define Package/python-cffi/description
Foreign Function Interface for Python calling C code.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="/usr" --root="$(PKG_INSTALL_DIR)")
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="/usr" --root="$(STAGING_DIR)/host")
endef

define Host/Install
endef

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-cffi))
$(eval $(call BuildPackage,python-cffi))
