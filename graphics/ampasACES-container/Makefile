# Created by: Rusmir Dusko <nemysis@FreeBSD.org>
# $FreeBSD$

PORTNAME=	ampasACES-container
PORTVERSION=	1.0.0
CATEGORIES=	graphics devel

MAINTAINER=	ports@FreeBSD.org
COMMENT=	ACES Container Reference Implementation

LICENSE=	AMPAS
LICENSE_NAME=	AMPAS
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

USE_GITHUB=	yes
GH_ACCOUNT=	ampas
GH_PROJECT=	aces_container
GH_TAGNAME=	${GH_COMMIT}
GH_COMMIT=	73f15c5

USES=		cmake pkgconfig
USE_LDCONFIG=	yes

PORTDOCS=	README.md

post-patch:
	@${REINPLACE_CMD} -e 's|lib/pkgconfig|libdata/pkgconfig|' \
		-e 's|lib/CMake|lib/cmake|' \
		${WRKSRC}/CMakeLists.txt

post-install:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
