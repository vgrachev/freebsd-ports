# Created by: Manuel Creach <manuel.creach@me.com>
# $FreeBSD$

PORTNAME=	libva-intel-driver
PORTVERSION=	1.5.0
CATEGORIES=	multimedia
MASTER_SITES=	http://www.freedesktop.org/software/vaapi/releases/${PORTNAME}/

MAINTAINER=	manuel.creach@me.com
COMMENT=	VAAPI intel driver

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libva.so:${PORTSDIR}/multimedia/libva
BUILD_DEPENDS=	${LOCALBASE}/include/linux/videodev2.h:${PORTSDIR}/multimedia/v4l_compat

USES=		compiler:c11 gmake libtool pkgconfig tar:bzip2
USE_GL=		gl
USE_AUTOTOOLS=	aclocal autoheader automake autoconf libtoolize
ACLOCAL_ARGS=	-I.
AUTOMAKE_ARGS=	--add-missing
USE_LDCONFIG=	yes

CPPFLAGS+=	-isystem${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

PLIST_FILES=	lib/va/i965_drv_video.so

.include <bsd.port.pre.mk>

post-patch:	.SILENT
	${REINPLACE_CMD} -e 's/-ldl//' \
		${WRKSRC}/src/Makefile.am
	${REINPLACE_CMD} -e 's|driverdir|& --define-variable prefix=${PREFIX}|' \
		${WRKSRC}/configure.ac

.include <bsd.port.post.mk>
