# Created by: gahr
# $FreeBSD$

PORTNAME=	aeskulap
PORTVERSION=	0.2.1
PORTREVISION=	5
CATEGORIES=	graphics
MASTER_SITES=	http://www.bms-austria.com/%7Epipelka/${PORTNAME}/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Medical image viewer

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libglademm-2.4.so:${PORTSDIR}/devel/libglademm24

USES=		desktop-file-utils gettext libtool pkgconfig
USE_GNOME=	gconfmm26 gtkmm24
GCONF_SCHEMAS=	aeskulap.schemas
USE_LDCONFIG=	${PREFIX}/lib/aeskulap

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-static
CPPFLAGS+=	-I${LOCALBASE}/include
LIBS+=		-L${LOCALBASE}/lib
INSTALL_TARGET=	install-strip

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/aeskulap/*.so

.include <bsd.port.mk>
