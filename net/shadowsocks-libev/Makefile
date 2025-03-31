# $OpenBSD: Makefile,v 1.0 2025/03/27 21:00:00 xiaoding Exp $

COMMENT =	lightweight tunnel proxy to bypass firewalls
DISTNAME =	shadowsocks-libev-3.3.5
REVISION =	3
CATEGORIES =	net

HOMEPAGE =	https://github.com/shadowsocks/shadowsocks-libev
MAINTAINER =	xiaoding+freebsd@xiaoding.org

# GPL-3.0
PERMIT_PACKAGE =	Yes
PERMIT_DISTFILES =	Yes

SITES =		https://github.com/shadowsocks/shadowsocks-libev/releases/download/v${DISTNAME:S/shadowsocks-libev-//}/
EXTRACT_SUFX =	.tar.gz

LIB_DEPENDS =	devel/libev \
		security/polarssl \
		devel/pcre \
		security/libsodium \
		net/libcares
BUILD_DEPENDS =	devel/autoconf \
		devel/automake \
		devel/libtool

WANTLIB +=	c ev mbedcrypto pcre sodium cares

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS =	--enable-shared \
			--with-ev=${LOCALBASE} \
			--with-mbedtls=${LOCALBASE} \
			--with-sodium=${LOCALBASE} \
			--with-pcre=${LOCALBASE} \
			--with-cares=${LOCALBASE} \
			--disable-documentation
CONFIGURE_ENV =	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib"

CONFIGURE_ENV += CFLAGS="-Dreallocf=realloc"

USE_GMAKE =	Yes
NO_TEST =	Yes


post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/etc/shadowsocks-libev
	${INSTALL_DATA} ${WRKSRC}/debian/config.json ${PREFIX}/etc/shadowsocks-libev/config.json.sample
	${INSTALL_DATA_DIR} ${PREFIX}/etc/rc.d
	${INSTALL} -m 755 ${FILESDIR}/rc.d.shadowsocks_libev ${PREFIX}/etc/rc.d/shadowsocks_libev

.include <bsd.port.mk>
