# $FreeBSD$

PORTNAME=	avidemux26
PORTVERSION=	${AVIDEMUX2_VERSION}
PORTREVISION=	3
CATEGORIES=	multimedia
PKGNAMESUFFIX=	-qt4

MAINTAINER=	multimedia@FreeBSD.org
COMMENT=	Simple GUI based video editor (QT4 UI)

LIB_DEPENDS=	libADM6avutil.so.52:${PORTSDIR}/multimedia/avidemux26

MASTERDIR=	${.CURDIR}/../avidemux26
PLIST=		${.CURDIR}/pkg-plist

.include "${MASTERDIR}/Makefile.common"

CMAKE_SOURCE_PATH=	${WRKSRC}/avidemux/qt4

CMAKE_ARGS+=	-DAVIDEMUX_SOURCE_DIR=${WRKSRC} -DAVIDEMUX_INSTALL_PREFIX:PATH="${PREFIX}"

post-configure: post-configure-common

.include <bsd.port.post.mk>
