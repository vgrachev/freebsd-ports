# Created by: Dmitry Sivachenko <demon@FreeBSD.org>
# $FreeBSD$

PORTNAME=	cld
PORTVERSION=	20150113
CATEGORIES=	devel python
MASTER_SITES=	${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	demon
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	chromium_compact_language_detector-${PORTVERSION}

MAINTAINER=	demon@FreeBSD.org
COMMENT=	Python bindings for compact language detector library

LICENSE=	BSD3CLAUSE

LIB_DEPENDS=	libcld2.so:${PORTSDIR}/devel/cld

USES=		python

PLIST_FILES=	%%PYTHON_SITELIBDIR%%/cld2.so %%PYTHON_SITELIBDIR%%/cld2full.so

post-patch:
	${REINPLACE_CMD} -e "s#\.\./cld2#${LOCALBASE}/include/cld#" ${WRKSRC}/setup.py ${WRKSRC}/setup_full.py

do-build:
	cd ${WRKSRC} && ${PYTHON_CMD} setup.py build
	cd ${WRKSRC} && ${PYTHON_CMD} setup_full.py build

do-install:
	cd ${WRKSRC} && ${PYTHON_CMD} setup.py install -c -O1 --prefix=${PREFIX} --root=${STAGEDIR}
	cd ${WRKSRC} && ${PYTHON_CMD} setup_full.py install -c -O1 --prefix=${PREFIX} --root=${STAGEDIR}

.include <bsd.port.mk>
