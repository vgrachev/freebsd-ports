# Created by: Greg Larkin <glarkin@FreeBSD.org>
# $FreeBSD$

PORTNAME=	batchmodify
PORTVERSION=	0.8.0.9694
PORTREVISION=	1
CATEGORIES=	www devel python
MASTER_SITES=	http://www.sourcehosting.net/freebsd/distfiles/ \
		LOCAL/glarkin
PKGNAMEPREFIX=	trac-
DISTNAME=	${PORTNAME}plugin-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Enables users to modify several tickets together at once

DEPRECATED=	This functionality was merged into Trac since version 1.0
EXPIRATION_DATE=	2015-04-08

RUN_DEPENDS+=	trac>=0.12:${PORTSDIR}/www/trac

USES=		python:2 zip

WRKSRC=		${WRKDIR}/${PORTNAME}plugin/0.12/trunk
USE_PYTHON=	distutils autoplist

.include <bsd.port.mk>
