# $OpenBSD$

COMMENT = fast tunnel proxy to bypass firewalls, Rust implementation

DISTNAME = shadowsocks-rust-1.23.0
CATEGORIES = net

HOMEPAGE = https://github.com/shadowsocks/shadowsocks-rust

MAINTAINER = zen <zen@xai.com>

# MIT license
PERMIT_PACKAGE = Yes

# Fetch from GitHub
MASTER_SITES = https://github.com/shadowsocks/shadowsocks-rust/releases/download/v${DISTNAME}/
EXTRACT_SUFX = .tar.gz

# Rust dependency
MODULES = lang/rust
BUILD_DEPENDS = ${MODRUST_BUILD_DEPENDS}
MODRUST_BUILD = Yes
MODRUST_FEATURES = local-tun,local-redir,local-dns,local-fake-dns

# No runtime library dependencies
RUN_DEPENDS = 

# Cargo build settings
CONFIGURE_STYLE = cargo
SEPARATE_BUILD = Yes

# Install binaries and configs
do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/target/release/sslocal ${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKBUILD}/target/release/ssserver ${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKBUILD}/target/release/ssmanager ${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKBUILD}/target/release/ssurl ${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKBUILD}/target/release/ssservice ${PREFIX}/bin/
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/shadowsocks-rust
	${INSTALL_DATA} ${WRKSRC}/examples/config.json ${PREFIX}/share/examples/shadowsocks-rust/

.include <bsd.port.mk>
