# Created by: edwin@mavetju.org
# $FreeBSD$

PORTNAME=	einstein
PORTVERSION=	2.0
PORTREVISION=	9
CATEGORIES=	games
MASTER_SITES=	http://games.flowix.com/files/einstein/
DISTNAME=	${PORTNAME}-${PORTVERSION}-src

MAINTAINER=	edwin@mavetju.org
COMMENT=	Remake of old DOS game Sherlock, which was inspired by Albert Einstein's puzzle

USE_SDL=	sdl ttf mixer
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

post-patch:
	${REINPLACE_CMD} \
		-e "s,@@STAGEDIR@@,${STAGEDIR}," \
		-e "s,@@PREFIX@@,${PREFIX}," \
		${WRKSRC}/Makefile

.include <bsd.port.mk>
