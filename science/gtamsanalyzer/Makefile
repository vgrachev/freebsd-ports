# Created by: gurkan@phys.ethz.ch
# $FreeBSD$

PORTNAME=	gtamsanalyzer
PORTVERSION=	0.42
PORTREVISION=	4
CATEGORIES=	science gnustep
MASTER_SITES=	SF/tamsys/gnustep%20tams/GTAMSAnalyzer%2${PORTVERSION}
DISTNAME=	GTAMSAnalyzer.src.${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Qualitative Research Software for the Free World for GNUstep

LICENSE=	GPLv2

USE_GNUSTEP=	yes
USE_GNUSTEP_BACK=	yes
USE_GNUSTEP_BUILD=	yes
USE_GNUSTEP_INSTALL=	yes

WRKSRC=	${WRKDIR}/${DISTNAME}/Source

post-patch:
	${RM} "${WRKSRC}/obj"
	@${REINPLACE_CMD} '/^GNUSTEP_INSTALLATION_DIR/ s|=|=$$(DESTDIR)|' \
		${WRKSRC}/GNUmakefile

.include <bsd.port.mk>
