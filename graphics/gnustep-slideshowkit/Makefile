# $FreeBSD$

PORTNAME=	slideshowkit
PORTVERSION=	0.0.1
PORTREVISION=	20050211
CATEGORIES=	graphics gnustep
MASTER_SITES=	http://download.gna.org/gsimageapps/
PKGNAMEPREFIX=	gnustep-
DISTNAME=	SlideShowKit-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	SlideShow Framework

USE_GNUSTEP=	yes
USE_GNUSTEP_BACK=	yes
USE_GNUSTEP_BUILD=	yes
USE_GNUSTEP_INSTALL=	yes
USE_GNUSTEP_LDCONFIG=	${GNUSTEP_LOCAL_LIBRARIES}

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/GNUstep/Local/Library/Libraries/libSlideShow.so

.include <bsd.port.mk>
