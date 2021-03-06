# Created by: Will Andrews <andrews@technologist.com>
# $FreeBSD$

PORTNAME=	gnofract4d
PORTVERSION=	3.14.1
PORTREVISION=	3
CATEGORIES=	graphics gnome
MASTER_SITES=	SF

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Weird GNOME fractal generator

LICENSE=	BSD3CLAUSE

LIB_DEPENDS=	libjpeg.so:${PORTSDIR}/graphics/jpeg \
		libpng.so:${PORTSDIR}/graphics/png

USES=		desktop-file-utils pathfix pkgconfig python shared-mime-info
USE_GNOME=	gnomeprefix intlhack libgnomeui pygtk2
USE_PYTHON=	distutils autoplist
USE_GCC=	yes

CFLAGS+=	-I${LOCALBASE}/include

PLIST_FILES=	man/man1/gnofract4d.1.gz

PORTDOCS=	README
OPTIONS_DEFINE=	DOCS

.include <bsd.port.options.mk>

post-patch:
	@${REINPLACE_CMD}  -e 's|/usr/include/|${LOCALBASE}/include/|; \
		/# doc files/,+2d; /"html"/,+1d' \
		${WRKSRC}/setup.py
	@${REINPLACE_CMD}  -e 's|"CC"|"${CC}"|; s|"gcc"|"${CC}"|' \
		${WRKSRC}/setup.py \
		${WRKSRC}/fract4d/test_fractconfig.py \
		${WRKSRC}/fract4d/fc.py
	@${REINPLACE_CMD} -e 's|gcc|${CC}|' \
		${WRKSRC}/fract4d/test_codegen.py \
		${WRKSRC}/fract4d/fractconfig.py

post-install:
.for l in fract4d_stdlib fract4dc
	${STRIP_CMD} ${STAGEDIR}${PYTHON_SITELIBDIR}/fract4d/${l}.so
.endfor

	${INSTALL_MAN} ${WRKSRC}/doc/${PORTNAME}.1 \
		${STAGEDIR}${MAN1PREFIX}/man/man1/

	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
