# Created by: lightside <lightside@gmx.com>
# $FreeBSD$

PORTNAME=	treesheets
PORTVERSION=	0.0.20150117
CATEGORIES=	deskutils

MAINTAINER=	lightside@gmx.com
COMMENT=	Free form data organizer

LICENSE=	ZLIB
LICENSE_FILE=	${WRKSRC}/ZLIB_LICENSE.txt

USE_GITHUB=	yes
GH_ACCOUNT=	aardappel
GH_COMMIT=	0191b1f
GH_TAGNAME=	${GH_COMMIT}

BUILD_WRKSRC=	${WRKSRC}/src
EXTRACT_AFTER_ARGS=	--exclude .gitignore

USES=		compiler:c++11-lib
USE_WX=		3.0+
WX_UNICODE=	yes

PORTDATA=	images
PORTDOCS=	docs *.html
PORTEXAMPLES=	*

PLIST_FILES=	bin/${PORTNAME} \
		share/pixmaps/${PORTNAME}.png

DESKTOP_ENTRIES="TreeSheets" "${COMMENT}" \
		"${PORTNAME}" "${PORTNAME}" \
		"Office;Utility;" true

OPTIONS_DEFINE=	DOCS EXAMPLES

.include <bsd.port.pre.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} < 900014
CXXFLAGS+=	-D__LONG_LONG_SUPPORTED
.endif

post-patch: .SILENT
	${REINPLACE_CMD} -e 's|sys->frame->exepath+L"|L"${DOCSDIR}|' \
		${BUILD_WRKSRC}/document.h
	${REINPLACE_CMD} -e 's|wxFileName(exename).GetPath()|L"${DATADIR}"|' \
		${BUILD_WRKSRC}/myframe.h
	${REINPLACE_CMD} -e 's|frame->exepath+L"/examples|L"${EXAMPLESDIR}|' \
		${BUILD_WRKSRC}/system.h

do-build:
	(cd ${BUILD_WRKSRC} && ${SETENV} ${MAKE_ENV} \
		${CXX} -std=c++11 ${CXXFLAGS} \
		-o ${PORTNAME} *.cpp `${WX_CONFIG} --cxxflags --libs all`)

do-install:
	${INSTALL_PROGRAM} ${BUILD_WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin
	(cd ${WRKSRC}/TS && ${COPYTREE_SHARE} "${PORTDATA}" ${STAGEDIR}${DATADIR})
	(cd ${WRKSRC}/TS && ${COPYTREE_SHARE} "${PORTDOCS}" ${STAGEDIR}${DOCSDIR})
	(cd ${WRKSRC}/TS/examples && ${COPYTREE_SHARE} "${PORTEXAMPLES}" \
		${STAGEDIR}${EXAMPLESDIR})
	${INSTALL_DATA} ${WRKSRC}/TS/images/icon32.png \
		${STAGEDIR}${PREFIX}/share/pixmaps/${PORTNAME}.png

.include <bsd.port.post.mk>
