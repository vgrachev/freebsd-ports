# Created by: Mike Krutov <neko@takino.org>
# $FreeBSD$

PORTNAME=	zathura-pdf-poppler
PORTVERSION=	0.2.5
PORTREVISION=	4
CATEGORIES=	graphics
MASTER_SITES=	http://pwmt.org/projects/zathura/plugins/download/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Poppler render PDF plugin for Zathura PDF viewer

LICENSE=	zlib
LICENSE_NAME=	zlib license
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror pkg-mirror auto-accept

LIB_DEPENDS=	libpoppler-glib.so:${PORTSDIR}/graphics/poppler-glib
BUILD_DEPENDS=	zathura:${PORTSDIR}/graphics/zathura
RUN_DEPENDS=	zathura:${PORTSDIR}/graphics/zathura

PLIST_FILES=	lib/zathura/pdf.so \
		share/applications/zathura-pdf-poppler.desktop

USE_GNOME=	glib20 gtk30
USES=		desktop-file-utils gmake pkgconfig

CONFLICTS=	zathura-pdf-mupdf-[0-9]*

PLIST_FILES=	lib/zathura/pdf.so \
		share/applications/zathura-pdf-poppler.desktop

post-install:
	${STRIP_CMD} ${STAGEDIR}${LOCALBASE}/lib/zathura/pdf.so

.include <bsd.port.mk>
